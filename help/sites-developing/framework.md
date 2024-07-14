---
title: Kader voor tags AEM
description: Inhoud labelen en de infrastructuur AEM tags toepassen gebruiken
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
feature: Developing,Tagging
exl-id: 53a37449-ef87-4fa6-82de-88fdc24cf988
solution: Experience Manager, Experience Manager Sites
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '1638'
ht-degree: 0%

---


# Kader voor tags AEM {#aem-tagging-framework}

Door tags toe te wijzen, kunt u inhoud indelen en ordenen. Tags kunnen worden geclassificeerd door een naamruimte en een taxonomie. Voor gedetailleerde informatie over het gebruik van tags:

* Zie het document [ Gebruikend Markeringen ](/help/sites-authoring/tags.md) voor informatie over het etiketteren van inhoud als inhoudauteur.
* Zie het document [ Beheersende Markeringen ](/help/sites-administering/tags.md) voor het perspectief van een beheerder over het creëren van en het leiden van markeringen, en waarop inhoudmarkeringen zijn toegepast.

Dit artikel richt zich op het onderliggende kader dat het etiketteren in AEM steunt en hoe te om het als ontwikkelaar te gebruiken.

## Inleiding {#introduction}

U kunt als volgt inhoud labelen en de infrastructuur voor AEM tags gebruiken:

* De markering moet als knoop van type `[cq:Tag](#tags-cq-tag-node-type)` onder de [ taxonomy wortelknoop bestaan.](#taxonomy-root-node)

* In het knooppunt `NodeType` met gecodeerde inhoud moet de [`cq:Taggable`](#taggable-content-cq-taggable-mixin) -mix zijn opgenomen.
* [`TagID`](#tagid) wordt toegevoegd aan de eigenschap [`cq:tags`](#tagged-content-cq-tags-property) van het inhoudsknooppunt en wordt omgezet in een knooppunt van het type ` [cq:Tag](#tags-cq-tag-node-type)` .

## tags:cq:type tagknooppunt  {#tags-cq-tag-node-type}

De declaratie van een tag wordt vastgelegd in de repository in een knooppunt van het type `cq:Tag` .

Een tag kan een eenvoudig woord zijn (bijvoorbeeld `sky` ) of een hiërarchische taxonomie vertegenwoordigen (bijvoorbeeld `fruit/apple` , wat zowel de generieke `fruit` als de specifiekere `apple` betekent).

Tags worden geïdentificeerd door een unieke TagID.

Een tag bevat optionele metagegevens, zoals een titel, gelokaliseerde titels en een beschrijving. De titel zou in gebruikersinterfaces in plaats van TagID, indien aanwezig moeten worden getoond.

Met het coderingsframework kunt u auteurs en sitebezoekers ook beperken tot het gebruik van specifieke, vooraf gedefinieerde tags.

### Tagkenmerken {#tag-characteristics}

* Het knooppunttype is `cq:Tag` n
* De naam van de knoop is een component van [ TagID ](#tagid).
* [ TagID ](#tagid) omvat altijd a [ namespace.](#tag-namespace)
* De eigenschap `jcr:title` (de titel die in de gebruikersinterface moet worden weergegeven) is optioneel.
* De eigenschap `jcr:description` is optioneel.
* Wanneer het bevatten van kindknopen, wordt de markering bedoeld als a [ containermarkering.](#container-tags)
* De markering wordt opgeslagen in de bewaarplaats onder een basisweg genoemd de [ taxonomie wortelknoop.](#taxonomy-root-node)

Omdat de markeringen eenvoudig knopen JCR zijn, moeten de knoopnamen zich aan de [ JCR noemende overeenkomst houden.](naming-conventions.md)

### TagID {#tagid}

Een TagID identificeert een pad dat wordt omgezet naar een tagknooppunt in de opslagplaats.

Typisch, is TagID een steno TagID die met namespace begint of het kan een absolute TagID zijn die van de [ taxonomy wortelknoop begint.](#taxonomy-root-node)

Wanneer inhoud wordt gelabeld en nog niet bestaat, wordt de eigenschap `[cq:tags](#tagged-content-cq-tags-property)` toegevoegd aan het inhoudsknooppunt en wordt de tagID toegevoegd aan de arraywaarde van de eigenschap `String` .

TagID bestaat uit a [ namespace ](#tag-namespace) die door lokale TagID wordt gevolgd. [ de markeringen van de Container ](#container-tags) hebben subtags die een hiërarchische orde in de taxonomie vertegenwoordigen. Subtags kunnen worden gebruikt om naar labels te verwijzen op dezelfde manier als elke lokale TagID. Inhoud bijvoorbeeld labelen met `fruit` is toegestaan, zelfs als het een containertag met subtags betreft, zoals `fruit/apple` en `fruit/banana` .

### Taxonomy Root Node {#taxonomy-root-node}

Het basisknooppunt van de taxonomie is het basispad voor alle tags in de gegevensopslagruimte. Het knooppunt van de taxonomiwortel mag geen knooppunt van het type `cq:Tag` zijn.

In AEM is het basispad `/content/cq:tags` en het basisknooppunt is van het type `cq:Folder` .

### Tagnaamruimte {#tag-namespace}

Met naamruimten kunt u items groeperen. Het meest gangbare geval bij gebruik is een naamruimte per site (bijvoorbeeld een openbare, interne en poortindeling) of per grotere toepassing (bijvoorbeeld WCM, Assets, Communities). Maar naamruimten kunnen voor verschillende andere behoeften worden gebruikt. Naamruimten worden in de gebruikersinterface gebruikt om alleen de subset van tags (dat wil zeggen tags van een bepaalde naamruimte) weer te geven die van toepassing is op de huidige inhoud.

De namespace van de markering is het eerste niveau in taxonomy subtree, die de knoop onmiddellijk onder de [ taxonomy wortelknoop ](#taxonomy-root-node) is. Een naamruimte is een knooppunt van het type `cq:Tag` waarvan het bovenliggende element geen knooppunttype `cq:Tag` is.

Alle tags hebben een naamruimte. Wanneer geen naamruimte is opgegeven, wordt de tag toegewezen aan de standaardnaamruimte, namelijk TagID `default` met de titel `Standard Tags` , dat wil zeggen `/content/cq:tags/default` .

### Containerlabels {#container-tags}

Een containertag is een knooppunt van het type `cq:Tag` dat een willekeurig aantal onderliggende knooppunten en type bevat, zodat het tagmodel kan worden verbeterd met aangepaste metagegevens.

Bovendien dienen containertags (of supertags) in een taxonomie als de subsumptie van alle subtags. Inhoud die is gelabeld met `fruit/apple` wordt bijvoorbeeld ook beschouwd als gelabeld met `fruit` . Als u dus zoekt naar inhoud die is gelabeld met `fruit` , wordt ook de inhoud gevonden die is gelabeld met `fruit/apple` .

### TagID&#39;s oplossen {#resolving-tagids}

Als TagID een dubbelepunt (`:`) bevat, scheidt de dubbele punt namespace van de markering of de subtaxonomie, die verder met schuine strepen (`/`) wordt gescheiden. Als de tagID geen dubbele punt heeft, wordt de standaardnaamruimte geïmpliceerd.

De standaardlocatie en de enige locatie voor tags is lager dan `/content/cq:tags` .

Code die verwijst naar niet-bestaande paden of paden die niet naar een knooppunt `cq:Tag` verwijzen, wordt als ongeldig beschouwd en wordt genegeerd.

In de volgende tabel ziet u een aantal voorbeeld-ID&#39;s, de bijbehorende elementen en de manier waarop de TagID wordt omgezet in een absoluut pad in de opslagplaats:

| TagID | Naamruimte | Lokale id | Containerlabels | Label blad | Absoluut tagpad opslagplaats |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | Geen | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | Geen | Geen | Geen, de naamruimte | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### Localisatie van tagtitel {#localization-of-tag-title}

Wanneer de tag de optionele titeltekenreeks ( `jcr:title` ) bevat, is het mogelijk de titel voor weergave te lokaliseren door de eigenschap `jcr:title.<locale>` toe te voegen.

Raadpleeg de volgende documenten voor meer informatie:

* [ Markeringen in Verschillende Talen ](/help/sites-developing/building.md#tags-in-different-languages), die gebruik van APIs beschrijft
* [ het Leiden Markeringen in Verschillende Talen ](/help/sites-administering/tags.md#managing-tags-in-different-languages), die gebruik van de het etiketteren console beschrijft

### Toegangsbeheer {#access-control}

De markeringen bestaan als knopen in de bewaarplaats onder de [ taxonomie wortelknoop ](#taxonomy-root-node). Het toestaan of ontkennen van auteurs en plaatsbezoekers om markeringen in een bepaalde namespace tot stand te brengen kan worden bereikt door aangewezen ACLs in de bewaarplaats te plaatsen.

Door het weigeren van leesmachtigingen voor bepaalde tags of naamruimten, wordt ook de mogelijkheid ingesteld om codes toe te passen op specifieke inhoud.

Een gebruikelijke praktijk omvat:

* De `tag-administrators` -groep/rol schrijftoegang toestaan tot alle naamruimten (toevoegen/wijzigen onder `/content/cq:tags` ). Deze groep wordt geleverd met AEM out-of-the-box.
* Gebruikers/auteurs toegang verlenen tot alle naamruimten die voor hen (meestal alle) leesbaar moeten zijn.
* Gebruikers/auteurs toegang toestaan tot naamruimten waar tags vrij kunnen worden gedefinieerd door gebruikers/auteurs (voeg een knooppunt toe onder `/content/cq:tags/some_namespace`)

## Tagable Content : cq:Tagable Mixin {#taggable-content-cq-taggable-mixin}

Voor toepassingsontwikkelaars om het etiketteren aan een inhoudstype vast te maken, moet de registratie van de knoop ([ CND ](https://jackrabbit.apache.org/jcr/node-type-notation.html)) `cq:Taggable` mengen of `cq:OwnerTaggable` mengen omvatten.

De `cq:OwnerTaggable` -mix, die overerft van `cq:Taggable` , geeft aan dat de inhoud kan worden geclassificeerd door de eigenaar/auteur. In AEM is het alleen een kenmerk van het knooppunt `cq:PageContent` . Het coderingsframework vereist de `cq:OwnerTaggable` -mix niet.

>[!NOTE]
>
>Het wordt aanbevolen alleen tags in te schakelen op het knooppunt op het hoogste niveau van een samengevoegd inhoudsitem (of op het knooppunt `jcr:content` ervan). Voorbeelden zijn:
>
>* Pagina&#39;s (`cq:Page`) waar de `jcr:content` knoop van type `cq:PageContent` is dat `cq:Taggable` mixin omvat
>* Assets ( `cq:Asset` ) waar het `jcr:content/metadata` -knooppunt altijd de `cq:Taggable` -mix heeft
>

### Node Type Notation (CND) {#node-type-notation-cnd}

In de gegevensopslagruimte bestaan definities van knooppunttypen als CND-bestanden. De aantekening CND wordt bepaald als deel van de documentatie JCR [ hier ](https://jackrabbit.apache.org/jcr/node-type-notation.html).

De belangrijkste definities voor de in AEM opgenomen knooppunttypen zijn:

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

## Tagged Content: cq:tags, eigenschap {#tagged-content-cq-tags-property}

De eigenschap `cq:tags` is een `String` -array die wordt gebruikt om een of meer TagID&#39;s op te slaan wanneer deze door auteurs of bezoekers van de site op inhoud worden toegepast. De eigenschap heeft alleen betekenis wanneer deze wordt toegevoegd aan een knooppunt dat met de `[cq:Taggable](#taggable-content-cq-taggable-mixin)` -mix is gedefinieerd.

>[!NOTE]
>
>Als u AEM coderingsfunctionaliteit wilt gebruiken, moeten aangepaste toepassingen alleen tageigenschappen definiëren als `cq:tags` .

## Labels verplaatsen en samenvoegen {#moving-and-merging-tags}

Het volgende is een beschrijving van de gevolgen in de bewaarplaats wanneer het bewegen van of het samenvoegen van markeringen gebruikend de [ etiketterende console ](/help/sites-administering/tags.md):

* Wanneer een tag A onder `/content/cq:tags` wordt verplaatst of samengevoegd met tag B:

   * Label A wordt niet verwijderd en krijgt een eigenschap `cq:movedTo` .
   * Label B wordt gemaakt (als er een verplaatsing was) en krijgt een eigenschap `cq:backlinks` .

* `cq:movedTo` verwijst naar label B.

   * Deze eigenschap betekent dat tag A is verplaatst of samengevoegd met tag B. Als tag B wordt verplaatst, wordt deze eigenschap dienovereenkomstig bijgewerkt. Tag A is dus verborgen en wordt alleen in de opslagplaats bewaard om tag-id&#39;s op te lossen in inhoudsknooppunten die verwijzen naar tag A. De opschoonfunctie voor ongewenste details verwijdert tags zoals tag A, als er geen inhoudsknooppunten meer naar wijzen.

   * Een speciale waarde voor de eigenschap `cq:movedTo` is `nirvana` . De tag wordt toegepast wanneer de tag wordt verwijderd, maar kan niet uit de repository worden verwijderd omdat er subtags zijn met een `cq:movedTo` die moeten worden bewaard.

  >[!NOTE]
  >
  >De eigenschap `cq:movedTo` wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
  >
  >1. De tag wordt gebruikt in inhoud (wat betekent dat deze een referentie heeft) of
  >1. De tag bevat onderliggende elementen die al zijn verplaatst.

* `cq:backlinks` houdt de verwijzingen in de andere richting. Dit betekent dat er een lijst wordt bijgehouden met alle tags die zijn verplaatst naar of samengevoegd met tag B. Dit is vooral nodig om de eigenschappen van `cq:movedTo` up-to-date te houden wanneer tag B ook wordt verplaatst/samengevoegd/verwijderd of als tag B wordt geactiveerd. In dat geval moeten alle tags voor de achtergrond ook worden geactiveerd.

  >[!NOTE]
  >
  >De eigenschap `cq:backlinks` wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
  >
  >1. De tag wordt gebruikt in inhoud (dit betekent dat deze een referentie heeft) OR
  >1. De tag bevat onderliggende elementen die al zijn verplaatst.

* Het lezen van een eigenschap `cq:tags` van een inhoudsknooppunt heeft de volgende resolutie:

   1. Als er geen overeenkomst is onder `/content/cq:tags` , wordt geen tag geretourneerd.

   1. Als de tag een eigenschap `cq:movedTo` heeft ingesteld, wordt de tag-id waarnaar wordt verwezen gevolgd.

      * Deze stap wordt herhaald zolang de volgende tag de eigenschap `cq:movedTo` heeft.

   1. Als de volgende tag geen eigenschap `cq:movedTo` heeft, wordt de tag gelezen.

* Als u de wijziging wilt publiceren wanneer een tag is verplaatst of samengevoegd, moeten het knooppunt `cq:Tag` en alle bijbehorende back-ups worden gerepliceerd. Dit wordt automatisch gedaan wanneer de markering in de console van het markeringsbeleid wordt geactiveerd.

* Later worden de oude verwijzingen automatisch gewist wanneer de eigenschap `cq:tags` van de pagina wordt bijgewerkt. Dit wordt geactiveerd omdat het omzetten van een verplaatste tag via de API de doeltag retourneert, waardoor de doeltag-id wordt opgegeven.

>[!NOTE]
>
>Het verplaatsen van tags verschilt van het migreren van tags.

## Migratie van tags {#tags-migration}

Sinds Adobe Experience Manager 6.4 worden -tags opgeslagen onder `/content/cq:tags` , terwijl eerdere versies -tags onder `/etc/tags` hebben opgeslagen.

Wanneer u een upgrade uitvoert van een AEM van een eerdere versie dan versie 6.4, moeten de tags worden gemigreerd naar `/content/cq:tags` . Zie [ Gemeenschappelijke Herstructurering van de Bewaarplaats in AEM 6.5 ](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#tags) voor meer informatie.
