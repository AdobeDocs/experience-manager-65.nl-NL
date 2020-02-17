---
title: Aangepaste zoekformulieren bijwerken
seo-title: Aangepaste zoekformulieren bijwerken
description: In dit artikel worden de aanpassingen beschreven die na een upgrade nodig zijn om de aangepaste zoekformulieren te laten werken.
seo-description: In dit artikel worden de aanpassingen beschreven die na een upgrade nodig zijn om de aangepaste zoekformulieren te laten werken.
uuid: 35b8fbb9-5951-4e1c-bf04-4471a55b9cb0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: a08cee9c-e981-4483-8bdc-e6353977f854
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Aangepaste zoekformulieren bijwerken{#upgrading-custom-search-forms}

In AEM 6.2 is de locatie waar de aangepaste zoekformulieren in de opslagplaats zijn opgeslagen, gewijzigd. Na de upgrade worden ze verplaatst van hun locatie in 6.1 naar:

* /apps/cq/gui/content/facets

naar een nieuwe locatie onder:

* /conf/global/settings/cq/search/facets

Daarom moeten de formulieren na een upgrade handmatig worden aangepast om te kunnen blijven werken.

Dit geldt voor nieuwe zoekformulieren en standaardformulieren die zijn aangepast.

Raadpleeg de documentatie over [zoekfactoren](/help/assets/search-facets.md)voor meer informatie.

## De eigenschap resourceType wijzigen {#changing-the-resourcetype-property}

Tenzij anders vermeld, vereisen de meeste aanpassingen die na de verbetering moeten worden gedaan het veranderen van het `sling:resourceType` bezit voor de gevormde Vormen van het Onderzoek. Dit is nodig, zodat de eigenschap naar de juiste locatie van het renderscript wijst.

U kunt de eigenschap als volgt wijzigen:

1. Open CRXDE Lite door naar `https://server:port/crx/de/index.jsp`
1. Blader naar de locatie van het knooppunt dat moet worden aangepast, zoals opgegeven in de lijst met [aangepaste zoekformulieren](/help/sites-deploying/upgrading-custom-search-forms.md#list-of-custom-search-forms) hieronder.
1. Klik op het knooppunt. In de juiste eigenschappen ruit, klik en wijzig het **verbinden:resourceType** bezit.
1. Sla de wijzigingen op door op de knop Alles **** opslaan te drukken.

## Lijst met aangepaste zoekformulieren {#list-of-custom-search-forms}

Hieronder vindt u een lijst met alle aangepaste zoekformulieren en de wijzigingen die u na de upgrade nodig hebt. Ze verwijzen naar de namen in `/conf/global/settings/cq/search/facets/sites/items`.

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

**** Handeling: Verwijder het knooppunt volledig.

### Andere voorvertoningen van Fulltext {#other-fulltext-predicates}

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

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorspellingen voor padbrowser {#path-browser-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
   <td>path</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/search/predicates/pathprepredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>common/admin/customsearch/search preates/pathpredicate</p> </td>
  </tr>
 </tbody>
</table>

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorwaarden labels {#tags-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
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

**** Handeling: Pas de eigenschap **resourceType** aan (voeg &quot;**/koraal**&quot; toe, zoals hierboven aangegeven op locatie 6.2).

### Voorspelling van paginastatus {#page-status-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
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

* Het `pagestatuspredicate` knooppunt verwijderen
* Knooppunt kopiëren

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/publishstatuspredicate`
   * to `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Knooppunt kopiëren

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/livecopystatuspredicate`
   * to `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Zorg ervoor u `listOrder` bezit voor de `analyticspredicate` knoop aan &quot;**8**&quot;plaatst. Dit is nodig om conflicten te voorkomen.

### Datumbereik {#date-range-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
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

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Verborgen filter {#hidden-filter}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
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

**** Handeling: Er is niets om aan te passen.

### Voorspelling van analysemogelijkheden {#analytics-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
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

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Bereik voorspellen {#range-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/rangepredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>siteadmin/admin/search panel/search preates/rangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

>[!NOTE]
>
>Opmerking: In tegenstelling tot 6.1, geeft het Predicate van de Waaier niet meer een markering in de onderzoeksbar terug.

### Eigenschappenvoorspelling opties {#options-property-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
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

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Predicate voor schuifregelaarbereik {#slider-range-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/sliderrangepredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>siteadmin/admin/search panel/search preates/sliderrangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorspeld voor componenten {#components-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
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

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorspelling auteur {#author-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/userpreate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>siteadmin/admin/search panel/search preates/userpreate</p> </td>
  </tr>
 </tbody>
</table>

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Sjabloonvoorspelling {#templates-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /><br /> </td>
   <td>n.v.t.</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/templatePrepreate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koral/</strong>siteadmin/admin/search panel/search preates/templatePredicate</p> </td>
  </tr>
 </tbody>
</table>

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

## Middelen Admin Search Rail {#assets-admin-search-rail}

De onderstaande knooppunten verwijzen naar de namen in `/conf/global/settings/dam/search/facets/assets/items`

### Fulltext Predicate met knooppuntnaam &quot;fulltext&quot; {#fulltext-predicate-with-node-name-fulltext-1}

| Knooppunt(en) in standaardzoekformulier in 6.1 | fulltext |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/fulltextpreate |
| Type bron in 6.2 | n.v.t. |

In 6.1 maakte het standaard fulltext predikaat deel uit van het onderzoeksformulier. In 6.2 is het volledige tekstveld vervangen door OmniSearch. Dit predikaat wordt programmatically overgeslagen en kan worden verwijderd.

**** Handeling: Verwijder het bovenstaande knooppunt.

### Voorspellingen voor padbrowser {#path-browser-predicates-1}

| Knooppunt(en) in standaardzoekformulier in 6.1 | padbrowser |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/pathbrowserpreate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/pathbrowserpredicate |

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### MIME-typevoorspelling {#mime-type-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | mimetype |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe, zoals op de hierboven aangegeven locatie 6.2).

### Voorspellingen voor bestandsgrootte {#file-size-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | filesize |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/filesizepredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search preates/sliderangepredicate |

**** Handeling: Pas de afbeelding aan `resourceType` zoals u hierboven op locatie 6.2 ziet.

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

*  Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe zoals hierboven aangegeven op locatie 6.2)

* Voeg een eigenschap `optionPaths` (van het type String) toe met de waarde: `/libs/dam/options/predicates/publish`

* Voeg `singleSelect` eigenschap toe met booleaanse waarde `true`.

### Statusvoorspelling {#status-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | status |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe zoals hierboven aangegeven op locatie 6.2)

### Voorspellingen voor verloopstatus {#expiry-status-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | expirystatus |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/expiredassetpredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/expiredassetpredicate |

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe zoals hierboven aangegeven op locatie 6.2)

### Voorspelden voor metagegevensgeldigheid {#metadata-validity-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | metadatavalidity |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe zoals hierboven aangegeven op locatie 6.2)

### Beoordelingsvoorspelling {#rating-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | beoordeling |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/rating predicates |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search preates/sliderangepredicate |

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe zoals hierboven aangegeven op locatie 6.2)

### Richtingsvoorspelling {#orientation-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | orientation |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/searchPreates/tagsfilterPreate |
| Type bron in 6.2 | cq/gui/components/koral/common/admin/customsearch/search preates/tagspredicate |

**Acties:**

*  Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe zoals hierboven aangegeven op locatie 6.2)

* Voeg een `fieldLabel` eigenschap toe met dezelfde waarde als de `text` eigenschap op hetzelfde knooppunt.

* Voeg een `emptyText` eigenschap toe met dezelfde waarde als de `text` eigenschap op hetzelfde knooppunt.

* Voeg een `rootPath` eigenschap toe met dezelfde waarde als de `optionPaths` eigenschap op hetzelfde knooppunt.

### Stijlvoorspelling {#style-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | stijl |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/searchPreates/tagsfilterPreate |
| Type bron in 6.2 | cq/gui/components/koral/common/admin/customsearch/search preates/tagspredicate |

**Acties:**

*  Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe zoals hierboven aangegeven op locatie 6.2)

* Voeg een `fieldLabel` eigenschap toe met dezelfde waarde als de `text` eigenschap op hetzelfde knooppunt.

* Voeg een `emptyText` eigenschap toe met dezelfde waarde als de `text` eigenschap op hetzelfde knooppunt.

* Voeg een `rootPath` eigenschap toe met dezelfde waarde als de `optionPaths` eigenschap op hetzelfde knooppunt.

### Voorspelden video-indeling {#video-format-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | videoFormat |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe zoals hierboven aangegeven op locatie 6.2)

### Voorspelling van hoofdmiddelen {#mainasset-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | hoofdmiddel |
|---|---|
| Type bron in 6.1 | graniet/ui/components/foundation/form/hidden |
| Type bron in 6.2 | graniet/ui/componenten/koraal/stichting/vorm/verborgen |

**** Handeling: Pas de `resourceType` eigenschap aan (voeg &quot;**/koraal**&quot; toe zoals hierboven aangegeven op locatie 6.2)
