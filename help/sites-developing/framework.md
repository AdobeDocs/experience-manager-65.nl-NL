---
title: Kader voor tags AEM
seo-title: Kader voor tags AEM
description: Inhoud labelen en gebruikmaken van de infrastructuur voor tags AEM
seo-description: Inhoud labelen en gebruikmaken van de infrastructuur voor tags AEM
uuid: f80a2cb1-359f-41dd-a70b-626d92cc3d4c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: f69db472-9f5c-4c0d-9292-2920ef69feeb
docset: aem65
feature: Tags
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 0%

---


# AEM Tagingframework {#aem-tagging-framework}

U kunt als volgt de inhoud labelen en de infrastructuur voor AEM tags gebruiken:

* De tag moet bestaan als een knooppunt van het type ` [cq:Tag](#tags-cq-tag-node-type)` onder het [taxonomy root node](#taxonomy-root-node)

* NodeType van het gecodeerde inhoudsknooppunt moet de [ `cq:Taggable`](#taggable-content-cq-taggable-mixin)-mix bevatten
* [TagID](#tagid) wordt toegevoegd aan de [ `cq:tags`](#tagged-content-cq-tags-property) eigenschap van het inhoudknooppunt en wordt omgezet in een knooppunt van het type ` [cq:Tag](#tags-cq-tag-node-type)`

## Tags: cq:Type tagknooppunt {#tags-cq-tag-node-type}

De declaratie van een tag wordt vastgelegd in de repository in een knooppunt van het type `cq:Tag.`

Een tag kan een eenvoudig woord zijn (bv. lucht) of een hiërarchische taxonomie (bv. fruit/appel, wat zowel de generieke vrucht als de specifiekere appel betekent).

Tags worden geïdentificeerd door een unieke TagID.

Een tag bevat optionele metagegevens, zoals een titel, gelokaliseerde titels en een beschrijving. De titel zou in gebruikersinterfaces in plaats van TagID, indien aanwezig moeten worden getoond.

Met het coderingsframework kunt u auteurs en sitebezoekers ook beperken tot het gebruik van specifieke, vooraf gedefinieerde tags.

### Tagkenmerken {#tag-characteristics}

* knooppunttype is `cq:Tag`
* knooppuntnaam is een component van ` [TagID](#tagid)`
* ` [TagID](#tagid)` bevat altijd een [naamruimte](#tag-namespace)

* optionele `jcr:title` eigenschap (de titel die in de UI moet worden weergegeven)

* optionele eigenschap `jcr:description`

* bij het bevatten van kindknopen, wordt bedoeld als [containermarkering](#container-tags)
* wordt opgeslagen in de repository onder een basispad dat de [taxonomy root node](#taxonomy-root-node) wordt genoemd

### TagID {#tagid}

Een TagID identificeert een pad dat wordt omgezet naar een tagknooppunt in de repository.

Typisch, is TagID een steno TagID die met namespace begint of het kan een absolute TagID zijn die van [taxonomy wortelknoop](#taxonomy-root-node) begint.

Wanneer inhoud wordt geëtiketteerd, als het nog niet bestaat, wordt het ` [cq:tags](#tagged-content-cq-tags-property)` bezit toegevoegd aan de inhoudsknoop en TagID wordt toegevoegd aan de de seriewaarde van het Koord van het bezit.

TagID bestaat uit een [namespace](#tag-namespace) die door lokale TagID wordt gevolgd. [Container-](#container-tags) tags die een hiërarchische volgorde in de taxonomie aangeven. Subtags kunnen worden gebruikt om naar labels te verwijzen op dezelfde manier als elke lokale TagID. Zo is het bijvoorbeeld toegestaan om inhoud met &quot;fruit&quot; te labelen, zelfs als het gaat om een containertag met sublabels, zoals &quot;fruit/appel&quot; en &quot;fruit/banaan&quot;.

### Taxonomie basisknooppunt {#taxonomy-root-node}

Het basisknooppunt van de taxonomie is het basispad voor alle tags in de gegevensopslagruimte. De taxonomy wortelknoop moet *not* een knoop van type `  cq   :Tag` zijn.

In AEM is het basispad `/content/  cq   :tags` en het basisknooppunt is van het type `  cq   :Folder`.

### Tagnaamruimte {#tag-namespace}

Met naamruimten kunt u items groeperen. Het meest gangbare gebruik-hoofdlettergebruik is het hebben van een naamruimte per (web)site (bijvoorbeeld public, internal en portal) of per grotere toepassing (bijvoorbeeld WCM, Assets, Communities), maar naamruimten kunnen worden gebruikt voor verschillende andere behoeften. Naamruimten worden in de gebruikersinterface gebruikt om alleen de subset van tags (d.w.z. tags van een bepaalde naamruimte) weer te geven die van toepassing is op de huidige inhoud.

De naamruimte van de tag is het eerste niveau in de taxonomy-substructuur. Dit is het knooppunt direct onder het [taxonomy-hoofdknooppunt](#taxonomy-root-node). Een naamruimte is een knooppunt van het type `cq:Tag` waarvan het bovenliggende element geen knooppunttype `cq:Tag`is.

Alle tags hebben een naamruimte. Als er geen naamruimte is opgegeven, wordt de tag toegewezen aan de standaardnaamruimte. Dit is TagID `default` (Titel is `Standard Tags),`dat is `/content/cq:tags/default.`

### Containercodes {#container-tags}

Een containertag is een knooppunt van het type `cq:Tag` dat een willekeurig aantal onderliggende knooppunten en type bevat, waardoor het mogelijk is het tagmodel te verbeteren met aangepaste metagegevens.

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
   <td><strong>Repository<br /> Absoluut tagpad</strong></td>
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
   <td>(geen)</td>
   <td>(geen)</td>
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

### Lokalisatie van tagtitel {#localization-of-tag-title}

Wanneer de tag de optionele titeltekenreeks ( `jcr:title`) bevat, is het mogelijk de titel voor weergave te lokaliseren door de eigenschap `jcr:title.<locale>` toe te voegen.

Zie voor meer informatie

* [Tags in verschillende talen](/help/sites-developing/building.md#tags-in-different-languages) , waarmee het gebruik van de API&#39;s wordt beschreven
* [Tags beheren in verschillende talen](/help/sites-administering/tags.md#managing-tags-in-different-languages) , waarmee het gebruik van de Tagingconsole wordt beschreven

### Toegangsbeheer {#access-control}

Tags bestaan als knooppunten in de opslagplaats onder het [taxonomy root node](#taxonomy-root-node). Het toestaan of ontkennen van auteurs en plaatsbezoekers om markeringen in een bepaalde namespace tot stand te brengen kan worden bereikt door aangewezen ACLs in de bewaarplaats te plaatsen.

Door het weigeren van leesmachtigingen voor bepaalde tags of naamruimten wordt ook de mogelijkheid bepaald om codes toe te passen op specifieke inhoud.

Een gebruikelijke praktijk omvat:

* Het toestaan van `tag-administrators` groep/rol schrijft toegang tot alle namespaces (voeg toe/wijzig onder `/content/cq:tags`). Deze groep wordt geleverd met AEM out-of-the-box.

* Gebruikers/auteurs toegang verlenen tot alle naamruimten die voor hen (meestal alle) leesbaar moeten zijn.
* Gebruikers/auteurs toegang toestaan tot die naamruimten waar tags vrij kunnen worden gedefinieerd door gebruikers/auteurs (add_node onder `/content/cq:tags/some_namespace`)

## Tagable Content: cq:Tagable Mixin {#taggable-content-cq-taggable-mixin}

Toepassingsontwikkelaars kunnen labels aan een inhoudstype koppelen als de registratie van het knooppunt ([CND](https://jackrabbit.apache.org/node-type-notation.html)) de `cq:Taggable`-mix of de `cq:OwnerTaggable`-mix bevat.

De `cq:OwnerTaggable` mix, die overerft van `cq:Taggable`, is bedoeld om aan te geven dat de inhoud kan worden geclassificeerd door de eigenaar/auteur. In AEM, is het slechts een attribuut van de `cq:PageContent` knoop. Het coderingsframework vereist geen `cq:OwnerTaggable`-mix.

>[!NOTE]
>
>Het wordt aanbevolen alleen tags in te schakelen op het knooppunt op het hoogste niveau van een samengevoegd inhoudsitem (of op het knooppunt jcr:content). Voorbeelden zijn:
>
>* pagina&#39;s ( `cq:Page`) waarbij het `jcr:content`knooppunt van het type `cq:PageContent` is, dat de `cq:Taggable`-mix bevat.
   >
   >
* elementen ( `cq:Asset`) waarbij het `jcr:content/metadata` knooppunt altijd de `cq:Taggable`-mix heeft.

>



### Node Type Notation (CND) {#node-type-notation-cnd}

Node Type definities bestaan in de bewaarplaats als Cnd- dossiers. De CND-notatie wordt gedefinieerd als onderdeel van de JCR-documentatie [hier](https://jackrabbit.apache.org/node-type-notation.html).

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

## Gelabelde inhoud: cq:eigenschap tags {#tagged-content-cq-tags-property}

De eigenschap `cq:tags` is een array String die wordt gebruikt om een of meer tagID&#39;s op te slaan wanneer deze door auteurs of sitebezoekers op inhoud worden toegepast. De eigenschap heeft alleen betekenis wanneer deze wordt toegevoegd aan een knooppunt dat is gedefinieerd met de `[cq:Taggable](#taggable-content-cq-taggable-mixin)`-mix.

>[!NOTE]
>
>Als u AEM tagfuncties wilt gebruiken, moeten aangepaste toepassingen alleen `cq:tags`-eigenschappen definiëren.

## Labels {#moving-and-merging-tags} verplaatsen en samenvoegen

Hieronder volgt een beschrijving van de effecten in de opslagplaats bij het verplaatsen of samenvoegen van tags met de [Tagingconsole](/help/sites-administering/tags.md):

* Wanneer een tag A wordt verplaatst of samengevoegd in tag B onder `/content/cq:tags`:

   * tag A wordt niet verwijderd en krijgt een eigenschap `cq:movedTo`.
   * tag B wordt gemaakt (in het geval van een verplaatsing) en krijgt een eigenschap `cq:backlinks`.

* `cq:movedTo` verwijst naar label B. Deze eigenschap betekent dat tag A is verplaatst of samengevoegd met tag B. Als tag B wordt verplaatst, wordt deze eigenschap dienovereenkomstig bijgewerkt. Tag A is dus verborgen en wordt alleen in de opslagplaats bewaard om tag-id&#39;s op te lossen in inhoudsknooppunten die verwijzen naar tag A. De opschoonfunctie voor ongewenste details verwijdert tags zoals tag A, als er geen inhoudsknooppunten meer naar wijzen.
Een speciale waarde voor de eigenschap `cq:movedTo` is `nirvana`: wordt toegepast wanneer de tag wordt verwijderd, maar niet kan worden verwijderd uit de repository omdat er subtags zijn met een `cq:movedTo` die moeten worden bewaard.

   >[!NOTE]
   >
   >De eigenschap `cq:movedTo` wordt alleen toegevoegd aan de verplaatste of samengevoegde tag als aan een van deze voorwaarden wordt voldaan:
   > 1. De tag wordt gebruikt in inhoud (wat betekent dat deze een referentie heeft) OR
   > 1. De tag bevat onderliggende elementen die al zijn verplaatst.


* `cq:backlinks` houdt de verwijzingen in de andere richting, d.w.z. het houdt een lijst bij van alle markeringen die zijn verplaatst naar of samengevoegd met markering B. Dit is vooral nodig om de  `cq:movedTo`eigenschappen up-to-date te houden wanneer tag B ook wordt verplaatst/samengevoegd/verwijderd of als tag B wordt geactiveerd. In dat geval moeten alle tags voor de achtergrond ook worden geactiveerd.

   >[!NOTE]
   >
   >De eigenschap `cq:backlinks` wordt alleen toegevoegd aan de verplaatste of samengevoegde tag als aan een van deze voorwaarden wordt voldaan:
   >
   > 1. De tag wordt gebruikt in inhoud (wat betekent dat deze een referentie heeft) OR    >
   > 1. De tag bevat onderliggende elementen die al zijn verplaatst.


* Wanneer u een eigenschap `cq:tags` van een inhoudsknooppunt leest, wordt het volgende opgelost:

   1. Als er geen overeenkomst onder `/content/cq:tags` is, wordt geen markering teruggekeerd.
   1. Als voor de tag een eigenschap `cq:movedTo` is ingesteld, wordt de tag-id waarnaar wordt verwezen gevolgd.
Deze stap wordt herhaald zolang de volgende markering een `cq:movedTo` bezit heeft.

   1. Als de volgende tag geen eigenschap `cq:movedTo` heeft, wordt de tag gelezen.

* Als u de wijziging wilt publiceren wanneer een tag is verplaatst of samengevoegd, moeten het knooppunt `cq:Tag` en alle bijbehorende back-ups worden gerepliceerd: dit wordt automatisch gedaan wanneer de markering in de console van het markeringsbeleid wordt geactiveerd.

* Later worden de &#39;oude&#39; verwijzingen automatisch aangepast aan de `cq:tags`-eigenschap van de pagina. Dit wordt geactiveerd omdat het omzetten van een verplaatste tag via de API de doeltag retourneert, waardoor de doeltag-id wordt opgegeven.

>[!NOTE]
>
>Het verplaatsen van tags verschilt van het migreren van tags.

## Migratie van labels {#tags-migration}

Vanaf Experience Manager 6.4 worden de markeringen opgeslagen onder `/content/cq:tags`, die vroeger onder `/etc/tags` werden opgeslagen. In scenario&#39;s waarin Adobe Experience Manager vanaf de vorige versie is bijgewerkt, zijn de tags echter nog steeds aanwezig op de oude locatie `/etc/tags`. In geüpgrade systemen moeten codes worden gemigreerd onder `/content/cq:tags`.

>[!NOTE]
>
>In Pagina-eigenschappen van de tagpagina wordt aangeraden de tag-id (`geometrixx-outdoors:activity/biking`) te gebruiken in plaats van het basispad van de tag hard te coderen (bijvoorbeeld `/etc/tags/geometrixx-outdoors/activity/biking`).
>
>Als u labels wilt vermelden, kunt u `com.day.cq.tagging.servlets.TagListServlet` gebruiken.

>[!NOTE]
>
>Het wordt aangeraden de API voor tagbeheer als bron te gebruiken.

### Als Bijgewerkte AEM-instantie de TagManager-API {#upgraded-instance-support-tagmanager-api} ondersteunt

1. Aan het begin van de component detecteert de API van TagManager of het een geüpgrade AEM-instantie is. In het geüpgrade systeem worden de tags opgeslagen onder `/etc/tags`.

1. De API TagManager wordt dan uitgevoerd in achterwaartse verenigbaarheidswijze, wat betekent API `/etc/tags` als basisweg gebruikt. Zo niet, dan wordt een nieuwe locatie `/content/cq:tags` gebruikt.

1. Werk de taglocatie bij.

1. Nadat u tags naar de nieuwe locatie hebt gemigreerd, voert u het volgende script uit:

```java
import org.apache.sling.api.resource.*
import javax.jcr.*

ResourceResolverFactory resourceResolverFactory = osgi.getService(ResourceResolverFactory.class);
ResourceResolver resolver = resourceResolverFactory.getAdministrativeResourceResolver(null);
Session session = resolver.adaptTo(Session.class);

def queryManager = session.workspace.queryManager;
def statement = "/jcr:root/content/cq:tags//element(*, cq:Tag)[jcr:contains(@cq:movedTo,\'/etc/tags\') or jcr:contains(@cq:backlinks,\'/etc/tags\')]";
def query = queryManager.createQuery(statement, "xpath");

println "query = ${query.statement}\n";

def tags = query.execute().getNodes();


tags.each { node ->
  def tagPath = node.path;
  println "tag = ${tagPath}";

  if(node.hasProperty("cq:movedTo") && node.getProperty("cq:movedTo").getValue().toString().startsWith("/etc/tags"))
    {
     def movedTo = node.getProperty("cq:movedTo").getValue().toString();

     println "cq:movedTo = ${movedTo} \n";

     movedTo = movedTo.replace("/etc/tags","/content/cq:tags");
     node.setProperty("cq:movedTo",movedTo);
     } else if(node.hasProperty("cq:backlinks")){

     String[] backLinks = node.getProperty("cq:backlinks").getValues();
     int count = 0;

     backLinks.each { value ->
             if(value.startsWith("/etc/tags")){
                     println "cq:backlinks = ${value}\n";
                     backLinks[count] = value.replace("/etc/tags","/content/cq:tags");
    }
             count++;
     }

    node.setProperty("cq:backlinks",backLinks);
  }
}
session.save();

println "---------------------------------Success-------------------------------------"
```

Het manuscript haalt al die markeringen die `/etc/tags` in de waarde van `cq:movedTo/cq:backLinks` bezit hebben. Vervolgens wordt de opgehaalde resultaatset doorlopen en worden de eigenschapswaarden `cq:movedTo` en `cq:backlinks` omgezet in `/content/cq:tags` paden (in het geval dat `/etc/tags` wordt gedetecteerd in de waarde).

### Indien geüpgrade AEM instantie wordt uitgevoerd op klassieke UI {#upgraded-instance-runs-classic-ui}

>[!NOTE]
>
>Klassieke UI is niet nul onderbreking volgzaam en steunt geen nieuw weg van de markeringsbasis. Als u klassieke UI wilt gebruiken dan `/etc/tags` moet worden gecreeerd gevolgd door `cq-tagging` componentenherstart.

In het geval van bijgewerkte AEM die door TagManager API worden gesteund en in Klassieke UI lopen:

1. Als verwijzingen naar het oude basispad voor tags `/etc/tags` zijn vervangen door tagId of een nieuwe taglocatie `/content/cq:tags` te gebruiken, kunt u tags migreren naar de nieuwe locatie `/content/cq:tags` in CRX, gevolgd door het opnieuw opstarten van de component.

1. Nadat u tags naar de nieuwe locatie hebt gemigreerd, voert u het bovenstaande script uit.
