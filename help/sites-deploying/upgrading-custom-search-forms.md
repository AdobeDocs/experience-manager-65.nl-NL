---
title: Aangepast zoeken in Forms bijwerken
seo-title: Aangepast zoeken in Forms bijwerken
description: In dit artikel worden de aanpassingen beschreven die na een upgrade nodig zijn om de aangepaste zoekformulieren te laten werken.
seo-description: In dit artikel worden de aanpassingen beschreven die na een upgrade nodig zijn om de aangepaste zoekformulieren te laten werken.
uuid: 35b8fbb9-5951-4e1c-bf04-4471a55b9cb0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: a08cee9c-e981-4483-8bdc-e6353977f854
feature: Bijwerken
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---


# Aangepast zoeken in Forms upgraden{#upgrading-custom-search-forms}

In AEM 6.2 is de locatie waar Customized Search Forms in de opslagplaats wordt opgeslagen, gewijzigd. Na de upgrade worden ze verplaatst van hun locatie in 6.1 naar:

* /apps/cq/gui/content/facets

naar een nieuwe locatie onder:

* /conf/global/settings/cq/search/facets

Daarom moeten de formulieren na een upgrade handmatig worden aangepast om te kunnen blijven werken.

Dit geldt zowel voor nieuwe Zoeken in Forms als voor standaard Forms die is aangepast.

Raadpleeg de documentatie over [Zoekfactoren](/help/assets/search-facets.md) voor meer informatie.

## De eigenschap resourceType wijzigen {#changing-the-resourcetype-property}

Tenzij anders vermeld, vereisen de meeste aanpassingen die na de verbetering moeten worden gedaan veranderend het `sling:resourceType` bezit voor de gevormde Forms van het douaneOnderzoek. Dit is nodig, zodat de eigenschap naar de juiste locatie van het renderscript wijst.

U kunt de eigenschap als volgt wijzigen:

1. CRXDE Lite openen door naar `https://server:port/crx/de/index.jsp` te gaan
1. Blader naar de locatie van het knooppunt dat moet worden aangepast, zoals opgegeven in de lijst met [Aangepaste zoekopdrachten in Forms](/help/sites-deploying/upgrading-custom-search-forms.md#list-of-custom-search-forms) hieronder.
1. Klik op het knooppunt. In de juiste eigenschappen ruit, klik en wijzig **sling:resourceType** bezit.
1. Sla ten slotte de wijzigingen op door op de knop **Alles opslaan** te drukken.

## Lijst met aangepaste zoekopdrachten in Forms {#list-of-custom-search-forms}

Hieronder vindt u een lijst met alle aangepaste Search Forms en de wijzigingen die deze nodig hebben na de upgrade. Zij verwijzen naar de namen in `/conf/global/settings/cq/search/facets/sites/items`.

### Fulltext Predicate met knooppuntnaam &quot;fulltext&quot; {#fulltext-predicate-with-node-name-fulltext}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1</td>
   <td>fulltext</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/search/predicates/fulltextpreate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td>n.v.t.</td>
  </tr>
 </tbody>
</table>

In AEM 6.1 maakte de standaard fulltext voorspelling deel uit van het zoekformulier. In 6.2 is het volledige tekstveld vervangen door OmniSearch. Dit predikaat wordt programmatically overgeslagen en kan worden verwijderd.

**Handeling:het knooppunt volledig** verwijderen.

### Andere Fulltext-voorspelling {#other-fulltext-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekopdracht Uit in 6.1</td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/search/predicates/fulltextpreate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>common/admin/customsearch/search preates/fulltextpreate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorspellingen voor padbrowser {#path-browser-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>path</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/search/predicates/pathprepredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>common/admin/customsearch/search preates/pathprepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorwaarden voor labels {#tags-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>tags</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/doorzoeken voorspelates/tagspredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>common/admin/customsearch/search preates/tagspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de eigenschap  **** resourceType aan (voeg &quot;**/koraal**&quot;toe zoals in de hierboven vermelde locatie 6.2).

### Voorspelling van paginastatus {#page-status-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>pagestatus prediken</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/pagestatus preate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td>n.v.t.</td>
  </tr>
 </tbody>
</table>

De paginatiestatus is vervangen door twee voorvertoningen van de eigenschap Opties, een voor publicatie en een voor LiveCopy-status.

**Acties:**

* Het knooppunt `pagestatuspredicate` verwijderen
* Knooppunt kopiëren

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/publishstatuspredicate`
   * tot `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Knooppunt kopiëren

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/livecopystatuspredicate`
   * tot `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Zorg ervoor u `listOrder` bezit voor `analyticspredicate` knoop aan &quot;**8**&quot;plaatst. Dit is nodig om conflicten te voorkomen.

### Datumbereikvoorspelling {#date-range-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>daterangepredicate</td>
  </tr>
  <tr>
   <td>Type bron in 6.1</td>
   <td>cq/gui/components/common/admin/customsearch/search/predicates/daterangepredicate</td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>common/admin/customsearch/search preates/daterangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Verborgen filter {#hidden-filter}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>type</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>graniet/ui/components/foundation/form/hidden</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>graniet/ui/components/foundation/form/hidden</p> </td>
  </tr>
 </tbody>
</table>

**Actie:** niets aan te passen.

### Voorspelling voor analysemogelijkheden {#analytics-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>analyticspredicaat</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/analyticspredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>siteadmin/admin/search panel/search preates/analyticspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Bereik voorspellen {#range-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/rangepredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>site-admin/admin/search panel/search predicates/rangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

>[!NOTE]
>
>Opmerking: In tegenstelling tot 6.1, geeft het Predicate van de Waaier niet meer een markering in de onderzoeksbar terug.

### Voorspelling van eigenschap Opties {#options-property-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/optionspredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>siteadmin/admin/search panel/search preates/optionspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorspelling van Slider-bereik {#slider-range-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/sliderrangepredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>site-admin/admin/search panel/search predicates/sliderrangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorspelde componenten {#components-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/componentspredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>siteadmin/admin/search panel/search preates/componentspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorspelling auteur {#author-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/userpreate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>site-admin/admin/search panel/search predicates/userpredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Sjabloonvoorspelling {#templates-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt/s in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/templatePrepreate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>site-admin/admin/search panel/search preates/templatePreate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

## Middelen Admin Search Rail {#assets-admin-search-rail}

De hieronder vermelde knooppunten verwijzen naar de namen in `/conf/global/settings/dam/search/facets/assets/items`

### Fulltext Predicate met knooppuntnaam &quot;fulltext&quot; {#fulltext-predicate-with-node-name-fulltext-1}

| Knooppunt(en) in standaardzoekformulier in 6.1 | fulltext |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/fulltextpreate |
| Type bron in 6.2 | n.v.t. |

In 6.1 maakte het standaard fulltext predikaat deel uit van het onderzoeksformulier. In 6.2 is het volledige tekstveld vervangen door OmniSearch. Dit predikaat wordt programmatically overgeslagen en kan worden verwijderd.

**Handeling:** Verwijder het bovenvermelde knooppunt.

### Voorspellingen voor padbrowser {#path-browser-predicates-1}

| Knooppunt(en) in standaardzoekformulier in 6.1 | padbrowser |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/pathbrowserpreate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/pathbrowserpredicate |

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### MIME-tekstvoorspelling {#mime-type-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | mimetype |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorspellingen voor bestandsgrootte {#file-size-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | filesize |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/filesizepredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search preates/sliderangepredicate |

**Actie:** Pas  `resourceType` zoals aangetoond in de 6.2 hierboven plaats aan.

### Voorspellingen voor laatste wijziging van element {#asset-last-modified-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | assetlastmodifiedpredikaat |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/assetlastmodifiedpredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/assetlastmodifiedpredicate |

Handeling: Pas de eigenschap resourceType aan (voeg &quot;/koral&quot; toe, bijvoorbeeld op de hierboven aangegeven locatie 6.2).

### Voorspelling publiceren {#publish-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | publish |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/publish predikate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/publish predikate |

**Acties:**

* Pas de eigenschap `resourceType` aan (voeg &quot;**/koral**&quot; toe, zoals op de hierboven aangegeven locatie 6.2)

* Voeg een `optionPaths` (van typeKoord) bezit met de waarde toe: `/libs/dam/options/predicates/publish`

* Voeg `singleSelect` eigenschap met booleaanse waarde `true` toe.

### Statusvoorspelling {#status-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | status |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2)

### Voorspellingen voor vervalstatus {#expiry-status-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | expirystatus |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/expiredassetpredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/expiredassetpredicate |

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2)

### Voorwaarden voor metagegevensgeldigheid {#metadata-validity-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | metadatavalidity |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2)

### Beoordelingsvoorspelling {#rating-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | beoordeling |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/rating predicates |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search preates/sliderangepredicate |

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2)

### Richtingsvoorspelling {#orientation-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | orientation |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/searchPreates/tagsfilterPreate |
| Type bron in 6.2 | cq/gui/components/koral/common/admin/customsearch/search preates/tagspredicate |

**Acties:**

* Pas de eigenschap `resourceType` aan (voeg &quot;**/koral**&quot; toe, zoals op de hierboven aangegeven locatie 6.2)

* Voeg een eigenschap `fieldLabel` met dezelfde waarde toe als de eigenschap `text` op hetzelfde knooppunt.

* Voeg een `emptyText` bezit met de waarde toe het zelfde als `text` bezit op de zelfde knoop.

* Voeg een eigenschap `rootPath` toe met dezelfde waarde als de eigenschap `optionPaths` op hetzelfde knooppunt.

### Stijlvoorspelling {#style-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | stijl |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/searchPreates/tagsfilterPreate |
| Type bron in 6.2 | cq/gui/components/koral/common/admin/customsearch/search preates/tagspredicate |

**Acties:**

* Pas de eigenschap `resourceType` aan (voeg &quot;**/koral**&quot; toe, zoals op de hierboven aangegeven locatie 6.2)

* Voeg een eigenschap `fieldLabel` met dezelfde waarde toe als de eigenschap `text` op hetzelfde knooppunt.

* Voeg een `emptyText` bezit met de waarde toe het zelfde als `text` bezit op de zelfde knoop.

* Voeg een eigenschap `rootPath` toe met dezelfde waarde als de eigenschap `optionPaths` op hetzelfde knooppunt.

### Voorspellingen voor video-indeling {#video-format-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | videoFormat |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2)

### Voorspelling hoofdmiddel {#mainasset-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | hoofdmiddel |
|---|---|
| Type bron in 6.1 | graniet/ui/components/foundation/form/hidden |
| Type bron in 6.2 | graniet/ui/componenten/koraal/stichting/vorm/verborgen |

**Handeling:** Pas de  `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2)
