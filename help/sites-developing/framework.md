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

* Zie het document [Tags gebruiken](/help/sites-authoring/tags.md) voor informatie over het labelen van inhoud als auteur van inhoud.
* Zie het document [Tags beheren](/help/sites-administering/tags.md) voor het standpunt van een beheerder over het maken en beheren van tags en waarop inhoudstags zijn toegepast.

Dit artikel richt zich op het onderliggende kader dat het etiketteren in AEM steunt en hoe te om het als ontwikkelaar te gebruiken.

## Inleiding {#introduction}

U kunt als volgt inhoud labelen en de infrastructuur voor AEM tags gebruiken:

* De tag moet bestaan als knooppunt van type `[cq:Tag](#tags-cq-tag-node-type)` onder de [taxonomie root node.](#taxonomy-root-node)

* Het knooppunt voor gecodeerde inhoud `NodeType` moet de [`cq:Taggable`](#taggable-content-cq-taggable-mixin) mixin.
* De [`TagID`](#tagid) wordt toegevoegd aan de inhoud van het knooppunt [`cq:tags`](#tagged-content-cq-tags-property) eigenschap en wordt omgezet in een knooppunt van het type ` [cq:Tag](#tags-cq-tag-node-type)`.

## tags:cq:type tagknooppunt  {#tags-cq-tag-node-type}

De declaratie van een tag wordt vastgelegd in de repository in een knooppunt van het type `cq:Tag`.

Een tag kan een eenvoudig woord zijn (bijvoorbeeld `sky`) of een hiërarchische taxonomie vertegenwoordigen (bijvoorbeeld `fruit/apple`, wat zowel generieke `fruit` en de meer specifieke `apple`).

Tags worden geïdentificeerd door een unieke TagID.

Een tag bevat optionele metagegevens, zoals een titel, gelokaliseerde titels en een beschrijving. De titel zou in gebruikersinterfaces in plaats van TagID, indien aanwezig moeten worden getoond.

Met het coderingsframework kunt u auteurs en sitebezoekers ook beperken tot het gebruik van specifieke, vooraf gedefinieerde tags.

### Tagkenmerken {#tag-characteristics}

* Node type is `cq:Tag`n
* Node name is een component van [TagID](#tagid).
* De [TagID](#tagid) bevat altijd een [naamruimte.](#tag-namespace)
* De `jcr:title` eigenschap (de titel die in de UI moet worden weergegeven) is optioneel.
* De `jcr:description` eigenschap is optioneel.
* Als onderliggende knooppunten worden opgenomen, wordt de tag aangeduid als een [containertag.](#container-tags)
* De tag wordt in de repository opgeslagen onder een basispad dat het basispad heet [taxonomie root node.](#taxonomy-root-node)

Omdat tags alleen JCR-knooppunten zijn, moeten de knooppuntnamen voldoen aan de [JCR-naamgevingsconventie.](naming-conventions.md)

### TagID {#tagid}

Een TagID identificeert een pad dat wordt omgezet naar een tagknooppunt in de opslagplaats.

De tagID is doorgaans een steno-tagID die begint met de naamruimte, of het kan een absolute tagID zijn die begint op het tabblad [taxonomie root node.](#taxonomy-root-node)

Als inhoud is gelabeld en nog niet bestaat, wordt het `[cq:tags](#tagged-content-cq-tags-property)` eigenschap wordt toegevoegd aan het inhoudsknooppunt en de TagID wordt toegevoegd aan de eigenschap `String` arraywaarde.

De tagID bestaat uit een [namespace](#tag-namespace) gevolgd door de lokale TagID. [Containerlabels](#container-tags) beschikken over subtags die een hiërarchische volgorde in de taxonomie aangeven. Subtags kunnen worden gebruikt om naar labels te verwijzen op dezelfde manier als elke lokale TagID. Inhoud bijvoorbeeld labelen met `fruit` is toegestaan, zelfs als het een containertag met subtags is, zoals `fruit/apple` en `fruit/banana`.

### Taxonomy Root Node {#taxonomy-root-node}

Het basisknooppunt van de taxonomie is het basispad voor alle tags in de gegevensopslagruimte. Het taxonomiwortelknooppunt mag geen knooppunt van het type zijn `cq:Tag`.

In AEM is het basispad `/content/cq:tags` en de hoofdnode is van het type `cq:Folder`.

### Tagnaamruimte {#tag-namespace}

Met naamruimten kunt u items groeperen. Het meest gangbare geval bij gebruik is een naamruimte per site (bijvoorbeeld een openbare, interne en poortindeling) of per grotere toepassing (bijvoorbeeld WCM, Middelen, Communities). Maar naamruimten kunnen voor verschillende andere behoeften worden gebruikt. Naamruimten worden in de gebruikersinterface gebruikt om alleen de subset van tags (dat wil zeggen tags van een bepaalde naamruimte) weer te geven die van toepassing is op de huidige inhoud.

De naamruimte van de tag is het eerste niveau in de taxonomy-substructuur. Dit is het knooppunt direct onder de [taxonomie-hoofdknooppunt](#taxonomy-root-node). A namespace is een knoop van type `cq:Tag` waarvan de ouder geen `cq:Tag` knooppunttype.

Alle tags hebben een naamruimte. Als er geen naamruimte is opgegeven, wordt de tag toegewezen aan de standaardnaamruimte, namelijk TagID `default` met de titel `Standard Tags`, dat wil zeggen: `/content/cq:tags/default`.

### Containerlabels {#container-tags}

Een containertag is een knooppunt van het type `cq:Tag` met een willekeurig aantal onderliggende knooppunten en een willekeurig type onderliggende knooppunten, waardoor het tagmodel kan worden verbeterd met aangepaste metagegevens.

Bovendien dienen containertags (of supertags) in een taxonomie als de subsumptie van alle subtags. Inhoud die bijvoorbeeld is gelabeld met `fruit/apple` wordt beschouwd als getagd met `fruit` ook. Met andere woorden, zoeken naar inhoud waaraan labels zijn toegevoegd `fruit` zou ook de inhoud vinden waaraan `fruit/apple`.

### TagID&#39;s oplossen {#resolving-tagids}

Als de tagID een dubbele punt bevat (`:`), scheidt de dubbele punt de naamruimte van de tag of subtaxonomie, die verder wordt gescheiden met schuine strepen (`/`). Als de tagID geen dubbele punt heeft, wordt de standaardnaamruimte geïmpliceerd.

De standaard en enige locatie voor tags is lager dan `/content/cq:tags`.

Label dat verwijst naar niet-bestaande paden of paden die niet verwijzen naar een `cq:Tag` knooppunt wordt als ongeldig beschouwd en wordt genegeerd.

In de volgende tabel ziet u een aantal voorbeeld-ID&#39;s, de bijbehorende elementen en de manier waarop de TagID wordt omgezet in een absoluut pad in de opslagplaats:

| TagID | Naamruimte | Lokale id | Containerlabels | Label blad | Absoluut tagpad opslagplaats |
|---|---|---|---|---|---|
| `dam:fruit/apple/braeburn` | `dam` | `fruit/apple/braeburn` | `fruit`, `apple` | `braeburn` | `/content/cq:tags/dam/fruit/apple/braeburn` |
| `color/red` | `default` | `color/red` | `color` | `red` | `/content/cq:tags/default/color/red` |
| `sky` | `default` | `sky` | Geen | `sky` | `/content/cq:tags/default/sky` |
| `dam:` | `dam` | Geen | Geen | Geen, de naamruimte | `/content/cq:tags/dam` |
| `/content/cq:tags/category/car` | `category` | `car` | `car` | `car` | `/content/cq:tags/category/car` |

### Localisatie van tagtitel {#localization-of-tag-title}

Wanneer de tag de optionele titeltekenreeks bevat ( `jcr:title`), is het mogelijk de titel voor weergave te lokaliseren door de eigenschap toe te voegen `jcr:title.<locale>`.

Raadpleeg de volgende documenten voor meer informatie:

* [Tags in verschillende talen](/help/sites-developing/building.md#tags-in-different-languages), waarin het gebruik van de API&#39;s wordt beschreven
* [Tags beheren in verschillende talen](/help/sites-administering/tags.md#managing-tags-in-different-languages), waarin het gebruik van de coderingsconsole wordt beschreven

### Toegangsbeheer {#access-control}

Tags bestaan als knooppunten in de opslagplaats onder [taxonomie-hoofdknooppunt](#taxonomy-root-node). Het toestaan of ontkennen van auteurs en plaatsbezoekers om markeringen in een bepaalde namespace tot stand te brengen kan worden bereikt door aangewezen ACLs in de bewaarplaats te plaatsen.

Door het weigeren van leesmachtigingen voor bepaalde tags of naamruimten, wordt ook de mogelijkheid ingesteld om codes toe te passen op specifieke inhoud.

Een gebruikelijke praktijk omvat:

* De `tag-administrators` groep/rol schrijven toegang tot alle namespaces (toevoegen/wijzigen onder `/content/cq:tags`). Deze groep wordt geleverd met AEM out-of-the-box.
* Gebruikers/auteurs toegang verlenen tot alle naamruimten die voor hen (meestal alle) leesbaar moeten zijn.
* Gebruikers/auteurs toegang toestaan tot naamruimten waar tags vrij kunnen worden gedefinieerd door gebruikers/auteurs (voeg een knooppunt toe onder `/content/cq:tags/some_namespace`)

## Tagable Content : cq:Tagable Mixin {#taggable-content-cq-taggable-mixin}

Als ontwikkelaars van toepassingen tags aan een inhoudstype willen koppelen, moet u de registratie van het knooppunt ([CND](https://jackrabbit.apache.org/jcr/node-type-notation.html)) moet de `cq:Taggable` mengen of `cq:OwnerTaggable` mixin.

De `cq:OwnerTaggable` mixin, dat overerft van `cq:Taggable`, is bedoeld om aan te geven dat de inhoud door de eigenaar/auteur kan worden geclassificeerd. In AEM is het alleen een kenmerk van de `cq:PageContent` knooppunt. De `cq:OwnerTaggable` Het coderingsframework vereist geen mixin.

>[!NOTE]
>
>Het wordt aanbevolen alleen labels in te schakelen op het knooppunt op het hoogste niveau van een samengevoegd inhoudsitem (of op het bijbehorende item `jcr:content` knooppunt). Voorbeelden zijn:
>
>* Pagina&#39;s (`cq:Page`) waarbij de `jcr:content`node is type `cq:PageContent` die de `cq:Taggable` mixen
>* Activa ( `cq:Asset`) waarbij de `jcr:content/metadata` node heeft altijd de `cq:Taggable` mixen
>

### Node Type Notation (CND) {#node-type-notation-cnd}

In de gegevensopslagruimte bestaan definities van knooppunttypen als CND-bestanden. De CND-notatie wordt gedefinieerd als onderdeel van de JCR-documentatie [hier](https://jackrabbit.apache.org/jcr/node-type-notation.html).

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

De `cq:tags` eigenschap is een `String` -array die wordt gebruikt om een of meer TagID&#39;s op te slaan wanneer deze door auteurs of bezoekers van de site op inhoud worden toegepast. De eigenschap heeft alleen betekenis wanneer deze wordt toegevoegd aan een knooppunt dat is gedefinieerd met het `[cq:Taggable](#taggable-content-cq-taggable-mixin)` mixin.

>[!NOTE]
>
>Als u AEM coderingsfunctionaliteit wilt gebruiken, mogen door aangepaste toepassingen alleen eigenschappen van tags worden gedefinieerd `cq:tags`.

## Labels verplaatsen en samenvoegen {#moving-and-merging-tags}

Hieronder volgt een beschrijving van de effecten in de repository wanneer u tags verplaatst of samenvoegt met behulp van de [tagconsole](/help/sites-administering/tags.md):

* Wanneer een tag A wordt verplaatst of samengevoegd met tag B onder `/content/cq:tags`:

   * Label A wordt niet verwijderd en krijgt een `cq:movedTo` eigenschap.
   * Label B wordt gemaakt (als er een verplaatsing heeft plaatsgevonden) en krijgt een `cq:backlinks` eigenschap.

* `cq:movedTo` verwijst naar label B.

   * Deze eigenschap betekent dat tag A is verplaatst of samengevoegd met tag B. Als tag B wordt verplaatst, wordt deze eigenschap dienovereenkomstig bijgewerkt. Tag A is dus verborgen en wordt alleen in de opslagplaats bewaard om tag-id&#39;s op te lossen in inhoudsknooppunten die verwijzen naar tag A. De opschoonfunctie voor ongewenste details verwijdert tags zoals tag A, als er geen inhoudsknooppunten meer naar wijzen.

   * Een speciale waarde voor de `cq:movedTo` eigenschap is `nirvana`. De tag wordt toegepast wanneer de tag wordt verwijderd, maar kan niet uit de repository worden verwijderd omdat er subtags zijn met een `cq:movedTo` dat moet worden bewaard.

  >[!NOTE]
  >
  >De `cq:movedTo` De eigenschap wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
  >
  >1. De tag wordt gebruikt in inhoud (wat betekent dat deze een referentie heeft) of
  >1. De tag bevat onderliggende elementen die al zijn verplaatst.

* `cq:backlinks` houdt de verwijzingen in de andere richting. Dit betekent dat er een lijst wordt bijgehouden met alle tags die zijn verplaatst naar of samengevoegd met tag B. Dit is meestal vereist om `cq:movedTo` eigenschappen zijn up-to-date wanneer tag B wordt verplaatst/samengevoegd/verwijderd of wanneer tag B wordt geactiveerd; in dat geval moeten ook alle tags met de achtergrond worden geactiveerd.

  >[!NOTE]
  >
  >De `cq:backlinks` De eigenschap wordt alleen aan de verplaatste of samengevoegde tag toegevoegd als aan een van deze voorwaarden wordt voldaan:
  >
  >1. De tag wordt gebruikt in inhoud (dit betekent dat deze een referentie heeft) OR
  >1. De tag bevat onderliggende elementen die al zijn verplaatst.

* Een `cq:tags` Voor eigenschap van een inhoudsknooppunt wordt de volgende resolutie gebruikt:

   1. Als er geen overeenkomst is onder `/content/cq:tags`, er wordt geen tag geretourneerd.

   1. Als de tag een `cq:movedTo` eigenschap ingesteld, wordt de tag-id waarnaar wordt verwezen gevolgd.

      * Deze stap wordt herhaald zolang de volgende tag een `cq:movedTo` eigenschap.

   1. Als de volgende tag geen `cq:movedTo` eigenschap, wordt de tag gelezen.

* Als u de wijziging wilt publiceren wanneer een tag is verplaatst of samengevoegd, gaat u naar `cq:Tag` node en al zijn backlinks moeten worden gerepliceerd. Dit wordt automatisch gedaan wanneer de markering in de console van het markeringsbeleid wordt geactiveerd.

* Later wordt de pagina bijgewerkt met `cq:tags` wijzigt de eigenschap automatisch de oude verwijzingen. Dit wordt geactiveerd omdat het omzetten van een verplaatste tag via de API de doeltag retourneert, waardoor de doeltag-id wordt opgegeven.

>[!NOTE]
>
>Het verplaatsen van tags verschilt van het migreren van tags.

## Migratie van tags {#tags-migration}

Sinds Adobe Experience Manager 6.4 worden tags opgeslagen onder `/content/cq:tags` overwegende dat eerdere versies labels hebben opgeslagen onder `/etc/tags`.

Tags moeten worden gemigreerd wanneer u een AEM upgradet vanaf een eerdere versie dan versie 6.4 `/content/cq:tags`. Zie [Herstructurering van de gemeenschappelijke opslagplaats in AEM 6.5](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#tags) voor meer informatie .
