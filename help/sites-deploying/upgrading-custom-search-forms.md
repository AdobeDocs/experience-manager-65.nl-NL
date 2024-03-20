---
title: Aangepast zoeken in Forms bijwerken
description: In dit artikel worden de aanpassingen beschreven die na een upgrade nodig zijn om de aangepaste zoekformulieren te laten werken.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
feature: Upgrading
exl-id: 797bbdf9-917a-4537-a5f9-bf2682db968b
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1797'
ht-degree: 0%

---

# Aangepast zoeken in Forms bijwerken{#upgrading-custom-search-forms}

In AEM 6.2 is de locatie waar Customized Search Forms in de opslagplaats wordt opgeslagen, gewijzigd. Na de upgrade worden ze verplaatst van hun locatie in 6.1 naar:

* /apps/cq/gui/content/facets

naar een nieuwe locatie onder:

* /conf/global/settings/cq/search/facets

Daarom moeten de formulieren na een upgrade handmatig worden aangepast om te kunnen blijven werken.

Dit geldt voor de nieuwe Search Forms en standaard Forms die zijn aangepast.

Zie de documentatie over [Zoeken in gezichten](/help/assets/search-facets.md).

## De eigenschap resourceType wijzigen {#changing-the-resourcetype-property}

Tenzij anders vermeld, vereisen de meeste aanpassingen die na de verbetering moeten worden gedaan het veranderen van `sling:resourceType` eigenschap voor de geconfigureerde aangepaste Search Forms. Dit is nodig, zodat de eigenschap naar de juiste locatie van het renderscript wijst.

U kunt de eigenschap als volgt wijzigen:

1. CRXDE Lite openen door naar `https://server:port/crx/de/index.jsp`
1. Blader naar de locatie van het knooppunt dat moet worden aangepast, zoals opgegeven in de lijst met [Aangepaste zoekfunctie Forms](/help/sites-deploying/upgrading-custom-search-forms.md#list-of-custom-search-forms) hieronder.
1. Klik op het knooppunt. Klik in het deelvenster met eigenschappen rechts op de knop **sling:resourceType** eigenschap.
1. Als laatste slaat u de wijzigingen op door op de knop **Alles opslaan** knop.

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
   <td>nvt</td>
  </tr>
 </tbody>
</table>

In AEM 6.1 maakte de standaard fulltext voorspelling deel uit van het zoekformulier. In 6.2 is het volledige tekstveld vervangen door OmniSearch. Dit predikaat wordt programmatically overgeslagen en kan worden verwijderd.

**Handeling:** Verwijder het knooppunt volledig.

### Andere voorvertoningen van Fulltext {#other-fulltext-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekopdracht Uit in 6.1</td>
   <td>nvt</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/search/predicates/fulltextpreate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>common/admin/customsearch/search preates/fulltextpreate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Voorspellingen voor padbrowser {#path-browser-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>pad</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/search/predicates/pathprepredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>common/admin/customsearch/search preates/pathprepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Voorwaarden voor tags {#tags-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>tags</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/common/admin/customsearch/doorzoeken voorspelates/tagspredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>common/admin/customsearch/search preates/tagspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de **resourceType** eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Voorspelling van paginastatus {#page-status-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>pagestatuspredikaat</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/pagestatus preate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td>nvt</td>
  </tr>
 </tbody>
</table>

De paginatiestatus is vervangen door twee voorvertoningen van de eigenschap Opties, een voor publicatie en een voor LiveCopy-status.

**Handelingen:**

* Verwijder de `pagestatuspredicate` node
* Knooppunt kopiëren

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/publishstatuspredicate`
   * tot `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Knooppunt kopiëren

   * `/libs/settings/cq/search/facets/sites/jcr:content/items/livecopystatuspredicate`
   * tot `/conf/global/settings/cq/search/facets/sites/jcr:content/items`

* Zorg ervoor dat u `listOrder` eigenschap voor de `analyticspredicate` knoop aan &quot;**8**&quot;. Dit is nodig om conflicten te voorkomen.

### Datumbereik {#date-range-predicates}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>daterangepredicate</td>
  </tr>
  <tr>
   <td>Type bron in 6.1</td>
   <td>cq/gui/components/common/admin/customsearch/search/predicates/daterangepredicate</td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>common/admin/customsearch/search preates/daterangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Verborgen filter {#hidden-filter}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
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

**Handeling:** Niets om aan te passen.

### Voorspelling van analysemogelijkheden {#analytics-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>analyticspredicaat</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/analyticspredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>locadmin/admin/search panel/search preates/analyticspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Bereik voorspellen {#range-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>nvt</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/rangepredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>siteadmin/admin/search panel/search preates/rangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

>[!NOTE]
>
>Opmerking: in tegenstelling tot 6.1 wordt met het voorspellende bereik niet langer een tag in de zoekbalk weergegeven.

### Eigenschappenvoorspelling opties {#options-property-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>nvt</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/optionspredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>locadmin/admin/search panel/search preates/optionspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Predicate voor schuifbereik {#slider-range-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>nvt</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/sliderrangepredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>siteadmin/admin/search panel/search preates/sliderrangepredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Voorspeld voor componenten {#components-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>nvt</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/componentspredicate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>locadmin/admin/search panel/search preates/componentspredicate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Voorspelling auteur {#author-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>nvt</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/userpreate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>siteadmin/admin/search panel/search preates/userpredikate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Sjabloonvoorspelling {#templates-predicate}

<table>
 <tbody>
  <tr>
   <td>Knooppunt(en) in standaardzoekformulier in 6.1<br /> <br /> </td>
   <td>nvt</td>
  </tr>
  <tr>
   <td><p>Type bron in 6.1</p> </td>
   <td><p>cq/gui/components/site-admin/admin/search panel/search preates/templatePrepreate</p> </td>
  </tr>
  <tr>
   <td>Type bron in 6.2</td>
   <td><p>cq/gui/components<strong>/koraal/</strong>siteadmin/admin/search panel/search preates/templatespreate</p> </td>
  </tr>
 </tbody>
</table>

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

## Middelen Admin Search Rail {#assets-admin-search-rail}

De onderstaande knooppunten verwijzen naar de namen in `/conf/global/settings/dam/search/facets/assets/items`

### Fulltext Predicate met knooppuntnaam &quot;fulltext&quot; {#fulltext-predicate-with-node-name-fulltext-1}

| Knooppunt(en) in standaardzoekformulier in 6.1 | fulltext |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/fulltextpreate |
| Type bron in 6.2 | nvt |

In 6.1 maakte het standaard fulltext predikaat deel uit van het onderzoeksformulier. In 6.2 is het volledige tekstveld vervangen door OmniSearch. Dit predikaat wordt programmatically overgeslagen en kan worden verwijderd.

**Handeling:** Verwijder het bovenstaande knooppunt.

### Voorspellingen voor padbrowser {#path-browser-predicates-1}

| Knooppunt(en) in standaardzoekformulier in 6.1 | padbrowser |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/pathbrowserpreate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/pathbrowserpredicate |

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### MIME-typevoorspelling {#mime-type-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | mimetype |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven aangegeven locatie 6.2).

### Voorspellingen voor bestandsgrootte {#file-size-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | bestandsgrootte |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/filesizepredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search preates/sliderangepredicate |

**Handeling:** Aanpassen `resourceType` zoals weergegeven op bovenstaande locatie 6.2.

### Voorspellingen voor laatste wijziging van element {#asset-last-modified-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | assetlastmodifiedpredikaat |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/assetlastmodifiedpredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/assetlastmodifiedpredicate |

Actie: Pas het resourceType-bezit aan (voeg &quot;/koral&quot;toe zoals in de 6.2 hierboven vermelde plaats).

### Voorspelling publiceren {#publish-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | publish |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/publish prepress |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/publish predikate |

**Handelingen:**

* Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven vermelde locatie 6.2)

* Een `optionPaths` (van het type String) eigenschap met de waarde: `/libs/dam/options/predicates/publish`

* Toevoegen `singleSelect` eigenschap met booleaanse waarde `true`.

### Statusvoorspelling {#status-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | status |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven vermelde locatie 6.2)

### Voorspellingen voor verloopstatus {#expiry-status-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | vervalstatus |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/expiredassetpredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/expiredassetpredicate |

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven vermelde locatie 6.2)

### Voorspelden voor metagegevensgeldigheid {#metadata-validity-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | metadatavaliditeit |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven vermelde locatie 6.2)

### Beoordelingsvoorspelling {#rating-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | beoordeling |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/rating predicates |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search preates/sliderangepredicate |

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven vermelde locatie 6.2)

### Richtingsvoorspelling {#orientation-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | oriëntatie |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/searchPreates/tagsfilterPreate |
| Type bron in 6.2 | cq/gui/components/koral/common/admin/customsearch/search preates/tagspredicate |

**Handelingen:**

* Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven vermelde locatie 6.2)

* Voeg een `fieldLabel` eigenschap met dezelfde waarde als de `text` eigenschap op hetzelfde knooppunt.

* Een `emptyText` eigenschap met dezelfde waarde als `text` eigenschap op hetzelfde knooppunt.

* Voeg een `rootPath` eigenschap met dezelfde waarde als `optionPaths` eigenschap op hetzelfde knooppunt.

### Stijlvoorspelling {#style-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | stijl |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/searchPreates/tagsfilterPreate |
| Type bron in 6.2 | cq/gui/components/koral/common/admin/customsearch/search preates/tagspredicate |

**Handelingen:**

* Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven vermelde locatie 6.2)

* Voeg een `fieldLabel` eigenschap met dezelfde waarde als de `text` eigenschap op hetzelfde knooppunt.

* Een `emptyText` eigenschap met dezelfde waarde als `text` eigenschap op hetzelfde knooppunt.

* Voeg een `rootPath` eigenschap met dezelfde waarde als `optionPaths` eigenschap op hetzelfde knooppunt.

### Voorspelden video-indeling {#video-format-predicates}

| Knooppunt(en) in standaardzoekformulier in 6.1 | videoFormat |
|---|---|
| Type bron in 6.1 | dam/gui/components/admin/customsearch/search voorspelates/optionspredicate |
| Type bron in 6.2 | dam/gui/koral/components/admin/customsearch/search voorspelates/optionspredicate |

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven vermelde locatie 6.2)

### Voorspelling van hoofdmiddelen {#mainasset-predicate}

| Knooppunt(en) in standaardzoekformulier in 6.1 | hoofdmiddel |
|---|---|
| Type bron in 6.1 | graniet/ui/components/foundation/form/hidden |
| Type bron in 6.2 | graniet/ui/componenten/koraal/stichting/vorm/verborgen |

**Handeling:** Pas de `resourceType` eigenschap (toevoegen &quot;**/koraal**&quot; zoals op de hierboven vermelde locatie 6.2)
