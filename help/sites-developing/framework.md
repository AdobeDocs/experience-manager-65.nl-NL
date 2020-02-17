---
title: AEM Tagging Framework
seo-title: AEM Tagging Framework
description: Inhoud labelen en de infrastructuur voor AEM-tags gebruiken
seo-description: Inhoud labelen en de infrastructuur voor AEM-tags gebruiken
uuid: f80a2cb1-359f-41dd-a70b-626d92cc3d4c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: f69db472-9f5c-4c0d-9292-2920ef69feeb
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# AEM Tagging Framework{#aem-tagging-framework}

Inhoud labelen en de infrastructuur voor AEM-tags gebruiken:

* De tag moet bestaan als een knooppunt van het type ` [cq:Tag](#tags-cq-tag-node-type)` onder de [taxonomy root node](#taxonomy-root-node)

* NodeType van het gelabelde inhoudsknooppunt moet de [ `cq:Taggable`](#taggable-content-cq-taggable-mixin) mix bevatten
* De [TagID](#tagid) wordt toegevoegd aan de [`cq:tags`](#tagged-content-cq-tags-property) eigenschap van het inhoudsknooppunt en wordt omgezet naar een knooppunt van het type ` [cq:Tag](#tags-cq-tag-node-type)`

## Tags: cq:Type tagknooppunt {#tags-cq-tag-node-type}

De declaratie van een tag wordt vastgelegd in de repository in een knooppunt van het type `cq:Tag.`

Een tag kan een eenvoudig woord zijn (bv. lucht) of een hiërarchische taxonomie (bv. fruit/appel, wat zowel de generieke vrucht als de specifiekere appel betekent).

Tags worden geïdentificeerd door een unieke TagID.

Een tag bevat optionele metagegevens, zoals een titel, gelokaliseerde titels en een beschrijving. De titel zou in gebruikersinterfaces in plaats van TagID, indien aanwezig moeten worden getoond.

Met het coderingsframework kunt u auteurs en sitebezoekers ook beperken tot het gebruik van specifieke, vooraf gedefinieerde tags.

### Tagkenmerken {#tag-characteristics}

* knooppunttype is `cq:Tag`
* de knooppuntnaam is een component van ` [TagID](#tagid)`
* bevat ` [TagID](#tagid)` altijd een [naamruimte](#tag-namespace)

* optionele `jcr:title` eigenschap (de titel die in de UI moet worden weergegeven)

* optionele `jcr:description` eigenschap

* als onderliggende knooppunten worden opgenomen, wordt dit een [containertag genoemd](#container-tags)
* wordt opgeslagen in de gegevensopslagruimte onder een basispad dat het [taxonomiwortelknooppunt wordt genoemd](#taxonomy-root-node)

### TagID {#tagid}

Een TagID identificeert een pad dat wordt omgezet naar een tagknooppunt in de repository.

Typisch, is TagID een steno TagID die met namespace begint of het kan een absolute TagID zijn die van de [taxonomie wortelknoop](#taxonomy-root-node)begint.

Wanneer inhoud wordt geëtiketteerd, als het nog niet bestaat, wordt het ` [cq:tags](#tagged-content-cq-tags-property)` bezit toegevoegd aan de inhoudsknoop en TagID wordt toegevoegd aan de de seriewaarde van het Koord van het bezit.

TagID bestaat uit een [naamruimte](#tag-namespace) gevolgd door de lokale TagID. [Containertags](#container-tags) hebben subtags die een hiërarchische volgorde in de taxonomie aangeven. Subtags kunnen worden gebruikt om naar labels te verwijzen op dezelfde manier als elke lokale TagID. Zo is het bijvoorbeeld toegestaan om inhoud met &quot;fruit&quot; te labelen, zelfs als het gaat om een containertag met sublabels, zoals &quot;fruit/appel&quot; en &quot;fruit/banaan&quot;.

### Taxonomy Root Node {#taxonomy-root-node}

Het basisknooppunt van de taxonomie is het basispad voor alle tags in de gegevensopslagruimte. Het knooppunt van de taxonomiwortel mag *geen* knooppunt van het type zijn `  cq   :Tag`.

In AEM is het basispad `/content/  cq   :tags` en het basisknooppunt van het type `  cq   :Folder`.

### Tagnaamruimte {#tag-namespace}

Met naamruimten kunt u items groeperen. Het meest gangbare gebruik-hoofdlettergebruik is het hebben van een naamruimte per (web)site (bijvoorbeeld public, internal en portal) of per grotere toepassing (bijvoorbeeld WCM, Assets, Communities), maar naamruimten kunnen worden gebruikt voor verschillende andere behoeften. Naamruimten worden in de gebruikersinterface gebruikt om alleen de subset van tags (d.w.z. tags van een bepaalde naamruimte) weer te geven die van toepassing is op de huidige inhoud.

De naamruimte van de tag is het eerste niveau in de taxonomy-substructuur, dat het knooppunt is dat zich direct onder het [taxonomy-hoofdknooppunt](#taxonomy-root-node)bevindt. Een naamruimte is een knooppunt van het type `cq:Tag` waarvan het bovenliggende element geen `cq:Tag`knooppunttype is.

Alle tags hebben een naamruimte. Als er geen naamruimte is opgegeven, wordt de tag toegewezen aan de standaardnaamruimte, namelijk TagID `default` (Titel is `Standard Tags),`dat `/content/cq:tags/default.`

### Containerlabels {#container-tags}

Een containertag is een knooppunt van het type `cq:Tag` dat een willekeurig aantal onderliggende knooppunten en type bevat, zodat het tagmodel kan worden verbeterd met aangepaste metagegevens.

Bovendien fungeren containercodes (of supercodes) in een taxonomie als de subsom van alle subcodes: Zo wordt bijvoorbeeld ook inhoud met fruit/appel als gelabeld met fruit beschouwd, d.w.z. dat het zoeken naar inhoud die alleen met fruit is gelabeld, ook de inhoud vindt die met fruit/appel is gelabeld.

### TagID&#39;s oplossen {#resolving-tagids}

Als de tag-id een dubbele punt &quot;:&quot; bevat, scheidt de dubbele punt de naamruimte van de tag of subtaxonomie, die vervolgens worden gescheiden met de normale slashes &quot;/&quot;. Als de tag-id geen dubbele punt heeft, wordt de standaardnaamruimte geïmpliceerd.

De standaard en enige locatie van tags is onder /content/cq:tags.

Code die verwijst naar niet-bestaande paden of paden die niet naar een cq:Tag-knooppunt verwijzen, wordt als ongeldig beschouwd en wordt genegeerd.

In de volgende tabel ziet u een aantal voorbeeld-ID&#39;s, de bijbehorende elementen en de manier waarop de TagID wordt omgezet in een absoluut pad in de opslagplaats:


In de volgende tabel ziet u een aantal voorbeeld-ID&#39;s, de bijbehorende elementen en de manier waarop de TagID wordt omgezet in een absoluut pad in de opslagplaats:
In de volgende tabel ziet u een aantal voorbeeld-ID&#39;s, de bijbehorende elementen en de manier waarop de TagID wordt omgezet in een absoluut pad in de opslagplaats:

<table>
 <tbody>
  <tr>
   <td><strong>TagID<br /> </strong></td>
   <td><strong>Naamruimte</strong></td>
   <td><strong>Lokale id</strong></td>
   <td><strong>Containertag(s)</strong></td>
   <td><strong>Tag Leaf</strong></td>
   <td><strong>Absoluut<br /> tagpad voor opslagplaats</strong></td>
  </tr>
  <tr>
   <td>dam:fruit/appel/braeburn</td>
   <td>dam</td>
   <td>fruit/appel/braeburn</td>
   <td>vruchten, appel</td>
   <td>braedoorn</td>
   <td>/content/cq:tags/dam/fruit/appel/braeburn</td>
  </tr>
  <tr>
   <td>kleur/rood</td>
   <td>default</td>
   <td>kleur/rood</td>
   <td>color</td>
   <td>rood</td>
   <td>/content/cq:tags/default/color/red</td>
  </tr>
  <tr>
   <td>lucht</td>
   <td>default</td>
   <td>lucht</td>
   <td>(none)</td>
   <td>lucht</td>
   <td>/content/cq:tags/default/sky</td>
  </tr>
  <tr>
   <td>dam:</td>
   <td>dam</td>
   <td>(none)</td>
   <td>(none)</td>
   <td>(geen, de naamruimte)</td>
   <td>/content/cq:tags/dam</td>
  </tr>
  <tr>
   <td>/content/cq:tags/category/car</td>
   <td>categorie</td>
   <td>auto</td>
   <td>auto</td>
   <td>auto</td>
   <td>/content/cq:tags/category/car</td>
  </tr>
 </tbody>
</table>

### Localisatie van tagtitel {#localization-of-tag-title}

Wanneer de tag de optionele titeltekenreeks ( `jcr:title`) bevat, is het mogelijk de titel voor weergave te lokaliseren door de eigenschap toe te voegen `jcr:title.<locale>`.

Zie voor meer informatie

* [Tags in verschillende talen](/help/sites-developing/building.md#tags-in-different-languages) , waarmee het gebruik van de API&#39;s wordt beschreven
* [Tags beheren in verschillende talen](/help/sites-administering/tags.md#managing-tags-in-different-languages) , waarmee het gebruik van de Tagingconsole wordt beschreven

### Toegangsbeheer {#access-control}

Tags bestaan als knooppunten in de opslagplaats onder het [hoofdknooppunt](#taxonomy-root-node)van de taxonomie. Het toestaan of ontkennen van auteurs en plaatsbezoekers om markeringen in een bepaalde namespace tot stand te brengen kan worden bereikt door aangewezen ACLs in de bewaarplaats te plaatsen.

Door het weigeren van leesmachtigingen voor bepaalde tags of naamruimten wordt ook de mogelijkheid bepaald om codes toe te passen op specifieke inhoud.

Een gebruikelijke praktijk omvat:

* Het toestaan van de `tag-administrators` groep/de rol schrijft toegang tot alle namespaces (voeg toe/wijzig onder `/content/cq:tags`). Deze groep wordt geleverd met AEM out-of-the-box.

* Gebruikers/auteurs toegang verlenen tot alle naamruimten die voor hen (meestal alle) leesbaar moeten zijn.
* Gebruikers/auteurs toegang toestaan tot naamruimten waar tags vrij door gebruikers/auteurs kunnen worden gedefinieerd (add_node onder `/content/cq:tags/some_namespace`)

## Tagable Content: cq:Tagable Mixin {#taggable-content-cq-taggable-mixin}

Toepassingsontwikkelaars kunnen codering aan een inhoudstype koppelen als de registratie ([CND](https://jackrabbit.apache.org/node-type-notation.html)) van het knooppunt de `cq:Taggable` mixin of de `cq:OwnerTaggable` mixin bevat.

De `cq:OwnerTaggable` mix, die overerft van `cq:Taggable`, is bedoeld om aan te geven dat de inhoud kan worden geclassificeerd door de eigenaar/auteur. In AEM is het alleen een kenmerk van het `cq:PageContent` knooppunt. Het `cq:OwnerTaggable` coderingskader vereist geen mixine.

>[!NOTE]
>
>Het wordt aanbevolen alleen tags in te schakelen op het knooppunt op het hoogste niveau van een samengevoegd inhoudsitem (of op het knooppunt jcr:content). Voorbeelden zijn:
>
>* pagina&#39;s ( `cq:Page`) waar het `jcr:content`knooppunt van het type is `cq:PageContent` dat de `cq:Taggable` mix bevat.
   >
   >
* assets ( `cq:Asset`) waarbij het `jcr:content/metadata` knooppunt altijd de `cq:Taggable` mixin heeft.
>



### Node Type Notation (CND) {#node-type-notation-cnd}

Node Type definities bestaan in de bewaarplaats als Cnd- dossiers. De CND-notatie wordt [hier](https://jackrabbit.apache.org/node-type-notation.html)gedefinieerd als onderdeel van de JCR-documentatie.

De belangrijkste definities voor de in de AEM opgenomen knooppunttypen zijn:

```xml
[cq:Tag] > mix:title, nt:base
    orderable
    - * (undefined) multiple
    - * (undefined)
    + * (nt:base) = cq:Tag version

[cq:Taggable]
    mixin
    - cq:tags (string) multiple

[cq:OwnerTaggable] > cq:Taggable
    mixin
```

## Gelabelde inhoud: cq:eigenschap tags {#tagged-content-cq-tags-property}

De `cq:tags` eigenschap is een array String die wordt gebruikt om een of meer tagID&#39;s op te slaan wanneer deze door auteurs of bezoekers van de site op inhoud worden toegepast. De eigenschap heeft alleen betekenis wanneer deze wordt toegevoegd aan een knooppunt dat met de ` [cq:Taggable](#taggable-content-cq-taggable-mixin)` mix is gedefinieerd.

>[!NOTE]
>
>Als u de functionaliteit voor AEM-tags wilt gebruiken, moeten aangepaste toepassingen alleen `cq:tags`tageigenschappen definiëren.

## Labels verplaatsen en samenvoegen {#moving-and-merging-tags}

Hieronder volgt een beschrijving van de effecten in de opslagplaats bij het verplaatsen of samenvoegen van tags met behulp van de [Tagingconsole](/help/sites-administering/tags.md):

* Wanneer een tag A wordt verplaatst of samengevoegd met tag B onder `/content/cq:tags`:

   * tag A wordt niet verwijderd en krijgt een `cq:movedTo` eigenschap.
   * tag B wordt gemaakt (in het geval van een verplaatsing) en krijgt een `cq:backlinks` eigenschap.

* `cq:movedTo` verwijst naar label B.
Deze eigenschap betekent dat tag A is verplaatst of samengevoegd met tag B. Als tag B wordt verplaatst, wordt deze eigenschap dienovereenkomstig bijgewerkt. Tag A is dus verborgen en wordt alleen in de opslagplaats bewaard om tag-id&#39;s op te lossen in inhoudsknooppunten die verwijzen naar tag A. De opschoonfunctie voor ongewenste details verwijdert tags zoals tag A, als er geen inhoudsknooppunten meer naar wijzen.
Een speciale waarde voor de `cq:movedTo` eigenschap is `nirvana`: wordt toegepast wanneer de tag wordt verwijderd, maar niet kan worden verwijderd uit de repository omdat er subtags zijn met een `cq:movedTo` die moet worden bewaard.

   >[!NOTE]
   >
   >De `cq:movedTo` eigenschap wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
   > 1. De tag wordt gebruikt in inhoud (wat betekent dat deze een referentie heeft) OR
   > 1. De tag bevat onderliggende elementen die al zijn verplaatst.


* `cq:backlinks` houdt de verwijzingen in de andere richting, d.w.z. het houdt een lijst bij van alle markeringen die zijn verplaatst naar of samengevoegd met markering B. Dit is vooral nodig om de `cq:movedTo`eigenschappen up-to-date te houden wanneer tag B ook wordt verplaatst/samengevoegd/verwijderd of als tag B wordt geactiveerd. In dat geval moeten alle tags voor de achtergrond ook worden geactiveerd.

   >[!NOTE]
   >
   >De `cq:backlinks` eigenschap wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
   > 1. De tag wordt gebruikt in inhoud (wat betekent dat deze een referentie heeft) OR
   > 1. De tag bevat onderliggende elementen die al zijn verplaatst.


* Wanneer u een `cq:tags` eigenschap van een inhoudsknooppunt leest, wordt het volgende opgelost:

   1. Als er geen overeenkomst onder `/content/cq:tags`is, wordt geen tag geretourneerd.
   1. Als de tag een `cq:movedTo` eigenschapset heeft, wordt de tag-id waarnaar wordt verwezen gevolgd.
Deze stap wordt herhaald zolang de volgende tag een `cq:movedTo` eigenschap heeft.

   1. Als de volgende tag geen `cq:movedTo` eigenschap heeft, wordt de tag gelezen.

* Als u de wijziging wilt publiceren wanneer een tag is verplaatst of samengevoegd, moeten het `cq:Tag` knooppunt en alle bijbehorende back-ups worden gerepliceerd: dit wordt automatisch gedaan wanneer de markering in de console van het markeringsbeleid wordt geactiveerd.

* Later worden de &#39;oude&#39; verwijzingen automatisch verwijderd als de `cq:tags` eigenschap van de pagina wordt bijgewerkt. Dit wordt geactiveerd omdat het omzetten van een verplaatste tag via de API de doeltag retourneert, waardoor de doeltag-id wordt opgegeven.
