---
title: Functies voor zoeken en promoten aan uw pagina toevoegen
seo-title: Functies voor zoeken en promoten aan uw pagina toevoegen
description: Door de zoek&promotiefuncties van uw website te integreren, kunt u de componenten Zoeken&Promoten gebruiken om functies aan uw pagina's toe te voegen, zoals trefwoordzoekopdracht, verfijning van zoekresultaten op de pagina en banners.
seo-description: Door de zoek&promotiefuncties van uw website te integreren, kunt u de componenten Zoeken&Promoten gebruiken om functies aan uw pagina's toe te voegen, zoals trefwoordzoekopdracht, verfijning van zoekresultaten op de pagina en banners.
uuid: 8cd3c143-cb0b-4eb0-931d-9d447ea3c950
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 968b9131-ccdf-4856-b504-bc1a44974980
docset: aem65
translation-type: tm+mt
source-git-commit: bcb1840d23ae538c183eecb0678b6a75d346aa50

---


# Functies voor zoeken en promoten aan uw pagina toevoegen{#adding-search-promote-features-to-your-page}

Met de componenten Zoeken&amp;promoveren kunt u de volgende functies aan uw pagina&#39;s toevoegen om de zoek- en promotiefuncties in uw website te integreren:

* Trefwoordzoekopdracht
* Pagina met zoekresultaten
* Zoekverfijning
* Banners

U kunt de zoek&amp;promoemogelijkheden alleen gebruiken als uw AEM-beheerder deze heeft ingeschakeld. Zie [Integreren met Adobe Search&amp;Promote](/help/sites-administering/search-and-promote.md).

Facetten worden geconfigureerd op de zoek&amp;promoeserver, net als de informatie die elke component verschaft. De volgende tabel bevat een korte beschrijving van elke component. De volgende secties verstrekken gedetailleerde informatie over hun gebruik.

<table>
 <tbody>
  <tr>
   <th>&amp;Onderdeel opwaarderen</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Banners</td>
   <td>Hiermee geeft u banneradvertenties weer. Banners worden geselecteerd op basis van gegevens die via Zoeken en bevorderen zijn verzameld.<br /> </td>
  </tr>
  <tr>
   <td>Broodkruimels</td>
   <td>Geeft het zoekwoord en de reeks filters weer die de gebruiker op de zoekresultaten heeft toegepast.</td>
  </tr>
  <tr>
   <td>Selectievakje List-Facet</td>
   <td>Een lijst met selectievakjes voor het selecteren van facetten voor het filteren van zoekresultaten.</td>
  </tr>
  <tr>
   <td>Vervolgkeuzefactor</td>
   <td>Een vervolgkeuzelijst met facetten voor het filteren van zoekresultaten.</td>
  </tr>
  <tr>
   <td>Koppelingslijstfacet</td>
   <td>Een lijst met facetkoppelingen voor het filteren van zoekresultaten.</td>
  </tr>
  <tr>
   <td>Paginering</td>
   <td>Hiermee regelt u het navigeren door pagina's met zoekresultaten.</td>
  </tr>
  <tr>
   <td>Resultaten</td>
   <td>Geeft de resultaten van een trefwoordzoekopdracht weer.</td>
  </tr>
  <tr>
   <td>Zoeken</td>
   <td>Hiermee voegt u een zoekveld aan de pagina toe.</td>
  </tr>
 </tbody>
</table>

## De pagina met zoekresultaten maken {#creating-the-search-results-page}

Gebruik de console van Websites WCM om een pagina tot stand te brengen voor het tonen van onderzoeksresultaten. De resultaten van een zoekopdracht vanuit een zoekcomponent kunnen op deze pagina worden weergegeven als deze dezelfde service Zoeken en bevorderen gebruikt.

De componenten waarmee gebruikers zoekresultaten kunnen bekijken, zijn Resultaten en Paginering. De component **Resultaten** heeft geen configureerbare eigenschappen in de modus Bewerken of Ontwerpen. De component Resultaten geeft alleen de zoekresultaten weer, die koppelingen naar andere pagina&#39;s bevatten, en geeft het aantal resultaten voor het trefwoord Zoeken weer.

![srchresultscomp](assets/srchresultscomp.png)

Met de component **Paginering** kunnen gebruikers door meerdere pagina&#39;s met zoekresultaten navigeren. De gebruiker kan het aantal pagina&#39;s zien, naar de volgende of vorige pagina gaan, een pagina selecteren om te openen, of alle resultaten op één pagina consolideren.

![semafoonlaag](assets/srchpagination.png)

U kunt de volgende componenteneigenschappen op Edit wijze vormen om runtime gedrag te controleren:

* Eén resultatenpagina verbergen: Selecteer deze optie om de besturingselementen voor paginanavigatie te verbergen wanneer de zoekopdracht één pagina met resultaten retourneert.
* Eerste/laatste verbergen: Selecteer deze optie om te voorkomen dat gebruikers naar de eerste of laatste pagina met resultaten gaan.
* Vorige/volgende verbergen: Hiermee bepaalt u of gebruikers door resultatenpagina&#39;s kunnen navigeren ten opzichte van de huidige pagina.
* Alle weergaven verbergen: Hiermee bepaalt u of de gebruiker alle zoekresultaten op één pagina kan samenvoegen. Gewoonlijk maakt het verstrekken van gepagineerde gegevens efficiënter gebruik van servermiddelen. Selecteer deze optie als u wilt voorkomen dat grote gegevenssets in één antwoordbericht worden overgedragen.

### Filteren van resultaten op facetten inschakelen {#enabling-the-filtering-of-results-by-facets}

U kunt gebruikers toestaan om onderzoeksresultaten door facetten te filtreren. Met de **componenten Facet** List, **Dropdown Facet** en Facet **Link List** kunnen gebruikers een of meer facetten selecteren om te filteren. Wanneer u deze componenten gebruikt, moet u ook de **component Breadcrubs** opnemen. Broodkruimels geven de huidige filters aan die worden gebruikt.

De componenten **van de Lijst van de Selectievakjes Facet**, **Dropdown Facet**, en van de Facet van de Lijst van de **Verbinding elk hebben de volgende eigenschappen die u op** Edit **** wijze vormt:

* **Naam** facet: De naam van het facet dat voor filters wordt gebruikt.

De component **Lijst van facetten** van de Checkbox toont een lijst van facetten met een begeleidende checkbox. Gebruik een facet **Lijst** selectievakje zodat gebruikers een subset van resultaten kunnen weergeven die items van meerdere facetten bevatten. Het **merk** is bijvoorbeeld geschikt omdat meerdere merken hetzelfde type product leveren.

Er wordt een selectievakje weergegeven voor elk facet dat aan een zoekresultaat is gekoppeld. Wanneer een gebruiker een selectievakje selecteert, wordt de pagina opnieuw geladen met een bijgewerkte resultatenset. Alle selectievakjes blijven op de pagina aanwezig, zodat klanten op elk gewenst moment facetten aan het filter kunnen toevoegen of eruit kunnen verwijderen:

![sandpcheckboxComp](assets/sandpcheckboxcomp.png)

Met de **component DropdownFacet** kunnen klanten een facetitem in een vervolgkeuzelijst selecteren. Deze component is handig wanneer u wilt dat klanten zich tegelijk op één facetitem richten. Bijvoorbeeld, is het facet van het Departement aangewezen voor het toelaten van klanten om productonderzoeken door geslacht te beperken. John zoekt naar *spijkerbroek* en filtert vervolgens op de afdeling Mannen.

De vervolgkeuzelijst wordt gevuld met de facetten die aan alle zoekresultaten zijn gekoppeld. Als u een item in de vervolgkeuzelijst selecteert, wordt de pagina opnieuw geladen met een bijgewerkte resultatenset. De punten in de drop-down lijst veranderen niet zodat de klanten van facet aan facet op elk ogenblik kunnen schakelen.

![sandpdropdownafdeling](assets/sandpdropdowndepartment.png)

De component van de Facet van de Lijst van de **Verbinding** laat klanten toe om hun nadruk op punten geleidelijk te beperken die onder veelvoudige facetleden of facetten worden gecategoriseerd.

De leden van Facet verschijnen als lijst van verbindingen. De tekst van elke koppeling is de naam van een facetlid dat is gekoppeld aan de huidige zoekresultaten. Wanneer een klant op een facetkoppeling klikt, wordt de pagina opnieuw geladen en wordt een subset van de zoekresultaten weergegeven. De lijst met koppelingen wordt dienovereenkomstig bijgewerkt, zodat de focus nog kleiner wordt.

![sandplinklistcomp](assets/sandplinklistcomp.png)

De koppelingen in de lijst veranderen ook wanneer een filter wordt toegepast van een ander type van de component Zoeken&amp;Bevorderen. Het gebruik van meerdere typen filtercomponenten kan effectieve filtercombinaties opleveren.

Met de **component Breadcrumbs** kunnen klanten de filters zien die momenteel op zoekresultaten worden toegepast, in de volgorde waarin ze zijn toegepast. Klanten kunnen op de items in de broodkruimel klikken om terug te keren naar die filtercombinatie.

![sandpbreadcrumbcomp](assets/sandpbreadcrumbcomp.png)

U kunt de volgende eigenschappen voor Breadcrubs op Edit wijze vormen om de blik van de component aan te passen:

* Scheidingsteken: Definieer de teken- of tekentekenreeks die moet fungeren als scheidingsteken tussen elke breadcrumb. In het veld Scheidingsteken kan elke tekenreeks als invoer worden geaccepteerd. De standaardinstelling is: &quot;>&quot; (zonder aanhalingstekens)
* Scheidingsteken navolgende: Definieer een teken- of tekentekenreeks die aan het einde van de breadcrumbs moet worden weergegeven. In het veld Scheidingsteken volgteken wordt elke tekenreeks als invoer geaccepteerd. De standaardinstelling voor deze waarde is *blank* (er wordt dus niets weergegeven aan het einde van de regel voor broodkruimels)

### Zoekvakken toevoegen {#adding-search-boxes}

Met de component Zoeken kunnen klanten trefwoordzoekopdrachten uitvoeren. Voeg componenten van het Onderzoek aan elke pagina toe waar u toegang tot het zoeken wilt verlenen.

Configureer de volgende eigenschappen in de modus Bewerken om het runtimegedrag te beheren:

* Pad naar resultatenpagina: Het pad naar de pagina waarop de zoekresultaten worden weergegeven.
* Automatisch aanvullen inschakelen: Selecteer deze optie om voorgestelde zoektrefwoorden weer te geven wanneer de klant in het zoekvak begint te typen.

![zandzoekopdracht](assets/sandpsearchcomp.png)

### banners toevoegen {#adding-banners}

De component Banners geeft banneradvertenties weer volgens de zoek&amp;promotiezoekopdrachten van de klant. De logica op de zoek&amp;vervangingsserver bepaalt welke banner moet worden weergegeven. Een zoekopdracht naar spijkerbroeken kan bijvoorbeeld tot gevolg hebben dat een modebanner wordt weergegeven. Door te filteren op de afdeling Mannen kan de keuze van de banner verder worden verfijnd.

De component Banners biedt een configureerbare eigenschap met de naam Bannergebied. Selecteer in de modus Bewerken een van de eigenschapswaarden om op te geven hoe de banner wordt weergegeven. De service Zoeken en bevorderen bepaalt de lijst met waarden die u kunt selecteren.

### Voorbeeld van zoek&amp;promotiezoekpagina {#example-search-promote-search-page}

In dit diagram worden de componenten weergegeven die aan een pagina worden toegevoegd om de onderstaande pagina met volledig functionele zoekresultaten te maken.

![1328213789109](assets/1328213789109.png) , ![sandbox-voorbeeld](assets/sandppageexample.png)
