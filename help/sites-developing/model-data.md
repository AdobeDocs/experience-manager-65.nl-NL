---
title: Gegevensmodellering - David Nuescheler's model
seo-title: Gegevensmodellering - David Nuescheler's model
description: Aanbevelingen van David Nuescheler voor het modelleren van inhoud
seo-description: Aanbevelingen van David Nuescheler voor het modelleren van inhoud
uuid: acb27e81-9143-4e0d-a37a-ba26491a841f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 39546c0a-b72f-42df-859b-98428ee0d5fb
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Gegevensmodellering - David Nuescheler&#39;s model{#data-modeling-david-nuescheler-s-model}

## Source {#source}

De volgende details zijn ideeën en opmerkingen van David Nuescheler.

David was mede-oprichter en CTO of Day Software AG, een toonaangevende leverancier van software voor contentbeheer en contentinfrastructuur, die in 2010 door Adobe werd aangeschaft. Hij is nu mede-chef en VP van de Technologie van de Onderneming bij Adobe en leidt ook de ontwikkeling van JSR-170, de toepassing van de Bewaarplaats van de Inhoud van Java (JCR) programmeringsinterface (API), de technologienorm voor inhoudsbeheer.

Meer updates zijn ook te vinden op [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

## Inleiding van David {#introduction-from-david}

In verschillende discussies heb ik kunnen vaststellen dat ontwikkelaars enigszins ongerust zijn over de kenmerken en functies die het JCR heeft voorgesteld op het gebied van contentmodellering. Er is nog geen gids en zeer weinig ervaring met het modelleren van inhoud in een opslagplaats en waarom het ene inhoudsmodel beter is dan het andere.

Terwijl in de relationele wereld de softwareindustrie veel ervaring heeft over hoe te om gegevens te modelleren, zijn wij nog in de vroege stadia voor de ruimte van de inhoudsbewaarplaats.

Ik wil deze leemte graag opvullen door mijn persoonlijke mening te geven over de manier waarop inhoud moet worden gemodelleerd, in de hoop dat dit ooit zou kunnen uitmonden in iets wat zinvoller is voor de gemeenschap van ontwikkelaars, en dat is niet alleen mijn mening, maar iets wat meer algemeen toepasbaar is. Denk eraan dat dit mijn eerste stap is.

>[!NOTE]
>
>Disclaimer: Deze richtsnoeren geven mijn persoonlijke, soms controversiële standpunten weer. Ik zie ernaar uit deze richtsnoeren te bespreken en te verfijnen.

## Zeven eenvoudige regels {#seven-simple-rules}

### Regel 1: Gegevens eerst, structuur later. Misschien. {#rule-data-first-structure-later-maybe}

#### Toelichting {#explanation-1}

Ik raad aan om me geen zorgen te maken over een gedeclareerde gegevensstructuur in ERD-zin. Aanvankelijk.

Leer om van nt te houden:ongestructureerde (&amp; vrienden) in ontwikkeling.

Ik denk dat Stefano dit ongeveer samenvat.

Mijn onderste regel: Structuur is duur en in veel gevallen is het volstrekt overbodig om de structuur expliciet aan de onderliggende opslag te declareren.

Er is een impliciet contract met betrekking tot de structuur die uw toepassing inherent gebruikt. Stel dat ik de wijzigingsdatum van een blogbericht opsla in een lastModified-eigenschap. Mijn App zal automatisch weten om de wijzigingsdatum van dat zelfde bezit opnieuw te lezen, is er echt geen behoefte om dat uitdrukkelijk te verklaren.

Verdere gegevensbeperkingen zoals verplichte beperkingen of type- en waardebeperkingen mogen alleen worden toegepast wanneer dit om redenen van gegevensintegriteit vereist is.

#### Voorbeeld {#example-1}

Het bovenstaande voorbeeld van het gebruik van een eigenschap `lastModified` Date op bijvoorbeeld het knooppunt &quot;blogbericht&quot; betekent niet echt dat er een speciale notatietype nodig is. Ik zou zeker in eerste instantie `nt:unstructured` voor mijn blogberichtknooppunten gebruiken. Omdat ik in mijn blogtoepassing alleen maar de laatste wijzigingsdatum ga weergeven (mogelijk &#39;bestellen door&#39;), kan het me nauwelijks schelen of het een Date is. Aangezien ik impliciet vertrouw op mijn blogtoepassing om er toch een &quot;datum&quot;te plaatsen, is het echt niet nodig om de aanwezigheid van een `lastModified` datum in de vorm van een nodetype te verklaren.

### Regel 2: Geef de inhoudshiërarchie de drijfveer, laat het niet gebeuren. {#rule-drive-the-content-hierarchy-don-t-let-it-happen}

#### Toelichting {#explanation-2}

De inhoudshiërarchie is een zeer waardevol middel. Laat het dus niet gewoon gebeuren, ontwerp het. Als u geen &quot;goede&quot;, mens-leesbare naam voor een knoop hebt, is dat waarschijnlijk iets dat u zou moeten heroverwegen. Willekeurige getallen zijn nauwelijks een &quot;goede naam&quot;.

Hoewel het bijzonder gemakkelijk kan zijn om een bestaand relationeel model in een hiërarchisch model snel te zetten, zou men in dat proces wat moeten denken.

In mijn ervaring als men aan toegangsbeheer en insluiting denkt gewoonlijk goede bestuurders voor de inhoudshiërarchie. Beschouw het als uw bestandssysteem. Gebruik zelfs bestanden en mappen om deze op uw lokale schijf te modelleren.

Persoonlijk geef ik in veel gevallen in eerste instantie de voorkeur aan hiërarchische conventies boven het nodetyping-systeem en stel ik het typen later in.

>[!CAUTION]
>
>De manier waarop een opslagplaats voor inhoud gestructureerd is, kan ook van invloed zijn op de prestaties. Voor de beste prestaties, zou het aantal kindknopen in bijlage aan individuele knopen in een inhoudsbewaarplaats over het algemeen niet 1&#39;000 moeten overschrijden.
>
>Zie [Hoeveel gegevens kan CRX behandelen?](https://helpx.adobe.com/experience-manager/kb/CrxLimitation.html) voor meer informatie .

#### Voorbeeld {#example-2}

Ik zou een eenvoudig blogsysteem als volgt modelleren. Let op: in eerste instantie geef ik niet eens om de nodetypes die ik op dit moment gebruik.

```xml
/content/myblog
/content/myblog/posts
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping

/content/myblog/comments/iphone_shipping/i_like_it_too
/content/myblog/comments/iphone_shipping/i_like_it_too/i_hate_it
```

Ik denk dat een van de dingen die duidelijk worden, is dat we allemaal de structuur van de inhoud begrijpen, gebaseerd op het voorbeeld zonder verdere uitleg.

Wat in eerste instantie onverwacht kan zijn, is waarom ik de &quot;commentaren&quot; niet zou opslaan met de &quot;post&quot;, die te wijten is aan toegangscontrole die ik op een redelijk hiërarchische manier zou willen toepassen.

Met behulp van het bovenstaande inhoudsmodel kan ik de &quot;anonieme&quot; gebruiker gemakkelijk toestaan om opmerkingen te maken, maar de anonieme gebruiker op een alleen-lezen basis voor de rest van de werkruimte houden.

### Regel 3: Werkruimten zijn voor clone(), merge() en update(). {#rule-workspaces-are-for-clone-merge-and-update}

#### Toelichting {#explanation-3}

Als u geen `clone()`, `merge()` of `update()` methodes in uw toepassing gebruikt, is één enkele werkruimte waarschijnlijk de manier om te gaan.

&quot;Overeenkomende knooppunten&quot; is een concept dat is gedefinieerd in de specificatie JCR. In principe worden knooppunten die dezelfde inhoud vertegenwoordigen, in verschillende zogenaamde werkruimten samengevoegd.

Het JCR introduceert het zeer abstracte concept van Werkruimten, dat veel ontwikkelaars onduidelijk laat over wat met hen te doen. Ik zou willen voorstellen om uw gebruik van werkruimten als volgt te testen.

Als u een aanzienlijke overlapping van &quot;overeenkomstige&quot;knopen (hoofdzakelijk de knopen met zelfde UUID) in veelvoudige werkruimten hebt, zet u waarschijnlijk werkruimten aan goed gebruik.

Als knooppunten niet overlappen met dezelfde UUID, maakt u waarschijnlijk misbruik van werkruimten.

De werkruimten zouden niet voor toegangsbeheer moeten worden gebruikt. Zichtbaarheid van inhoud voor een bepaalde groep gebruikers is geen goed argument om dingen in verschillende werkruimten te scheiden. JCR heeft &#39;Toegangsbeheer&#39; in de opslagplaats voor inhoud om dat mogelijk te maken.

De werkruimten zijn de grens voor verwijzingen en vraag.

#### Voorbeeld {#example-3}

Werkruimten gebruiken voor bijvoorbeeld:

* v1.2 van uw project vs. a v1.3 van uw project
* een &quot;ontwikkeling&quot;, &quot;kwaliteitscontrole&quot; en een &quot;gepubliceerde&quot; inhoudsstatus

Gebruik geen werkruimten voor bijvoorbeeld:

* thuismappen van gebruiker
* duidelijke inhoud voor verschillende doelgroepen, zoals publiek, privé, lokaal, ...
* postvakken voor verschillende gebruikers

### Regel 4: Houd rekening met dezelfde naam. {#rule-beware-of-same-name-siblings}

#### Toelichting {#explanation-4}

Terwijl de Vergelijkende Naam Siblings (SNS) in de specificatie zijn geïntroduceerd om verenigbaarheid met gegevensstructuren toe te staan die voor en uitgedrukt door XML worden ontworpen en daarom uiterst waardevol voor JCR zijn, komt SNS met een aanzienlijke overheadkosten en ingewikkeldheid voor de bewaarplaats.

Om het even welk weg in de inhoudsbewaarplaats die SNS in één van zijn wegsegmenten bevat wordt veel minder stabiel, als SNS wordt verwijderd of opnieuw in orde gebracht, heeft het een effect op de wegen van alle andere SNS en hun kinderen.

Voor de invoer van XML of interactie met bestaande SNS van XML kunnen noodzakelijk en nuttig zijn maar ik heb nooit SNS gebruikt, en nooit in mijn &quot;groene gebied&quot;gegevensmodellen.

#### Voorbeeld {#example-4}

Gebruiken

```xml
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping
```

in plaats van

```xml
/content/blog[1]/post[1]
/content/blog[1]/post[2]
```

### Regel 5: Verwijzingen die als schadelijk worden beschouwd. {#rule-references-considered-harmful}

#### Toelichting {#explanation-5}

Referenties impliceren referentiële integriteit. Ik vind het belangrijk om te begrijpen dat verwijzingen niet alleen extra kosten voor de bewaarplaats toevoegen die de referentiële integriteit beheren, maar ook uit een oogpunt van inhoudflexibiliteit duur zijn.

Persoonlijk zorg ik ervoor ik slechts verwijzingen gebruik wanneer ik echt niet met een gevaarlijke verwijzing kan behandelen en anders een weg, een naam of een koordUID om naar een andere knoop te verwijzen.

#### Voorbeeld {#example-5}

Laten we aannemen dat ik &quot;verwijzingen&quot; van een document (a) naar een ander document (b) toestaat. Als ik deze relatie modelleer met behulp van referentie-eigenschappen, betekent dit dat de twee documenten zijn gekoppeld op het niveau van de gegevensopslagruimte. Ik kan document (a) niet afzonderlijk exporteren/importeren, omdat het doel van de referentie-eigenschap mogelijk niet bestaat. Andere bewerkingen, zoals samenvoegen, bijwerken, herstellen of klonen, worden ook beïnvloed.

Dus ik zou deze verwijzingen modelleren als &quot;zwakke verwijzingen&quot; (in JCR v1.0 komt dit in feite neer op tekenreekseigenschappen die de uuid van het doelknooppunt bevatten) of eenvoudig een pad gebruiken. Soms is het pad zinvoller om mee te beginnen.

Ik denk dat er gevallen zijn waarin een systeem echt niet kan werken als een verwijzing gevaarlijk is, maar ik kan gewoon niet met een goed &quot;echt&quot; maar simpel voorbeeld komen uit mijn directe ervaring.

### Regel 6: Bestanden zijn bestanden. {#rule-files-are-files}

#### Toelichting {#explanation-6}

Als een inhoudsmodel iets blootstelt dat zelfs ver als een dossier of een omslag *ruikt* ik probeer te gebruiken (of zich uit) `nt:file`, `nt:folder` en `nt:resource`.

In mijn ervaring staan veel generieke toepassingen interactie met nt:folder en nt:dossiers impliciet toe en weten hoe te om die gebeurtenis te behandelen en te tonen als zij met extra meta-informatie worden verrijkt. Zo wordt een directe interactie met bestandsserverimplementaties, zoals CIFS of WebDAV die boven op de JCR zitten, impliciet.

Ik denk dat als goede duim men het volgende zou kunnen gebruiken: Als u de bestandsnaam en het mime-type moet opslaan, `nt:file`/ `nt:resource` is een zeer goede overeenkomst. Als u meerdere &quot;bestanden&quot; zou kunnen hebben, is de map nt:een goede plaats om deze op te slaan.

Als u meta-informatie voor uw middel moet toevoegen, zeggen &quot;auteur&quot;of een &quot;beschrijving&quot;bezit, breid `nt:resource` niet uit `nt:file`. Ik breid zelden &#39;nt:file&#39; uit en breid vaak uit `nt:resource`.

#### Voorbeeld {#example-6}

Laten we aannemen dat iemand een afbeelding naar een blogbericht wil uploaden op:

```xml
/content/myblog/posts/iphone_shipping
```

en misschien zou de eerste darmreactie bestaan uit het toevoegen van een binaire eigenschap met het beeld.

Hoewel er zeker goede gebruiksgevallen zijn om enkel een binair bezit te gebruiken (laten wij zeggen de naam irrelevant is en mime-type impliciet is) in dit geval zou ik de volgende structuur voor mijn blogvoorbeeld adviseren.

```xml
/content/myblog/posts/iphone_shipping/attachments [nt:folder]
/content/myblog/posts/iphone_shipping/attachments/front.jpg [nt:file]
/content/myblog/posts/iphone_shipping/attachments/front.jpg/jcr:content [nt:resource]
```

### Regel 7:Id&#39;s zijn slecht. {#rule-ids-are-evil}

#### Toelichting {#explanation-7}

In relationele databases zijn id&#39;s een noodzakelijke manier om relaties tot stand te brengen, zodat mensen ze ook in inhoudsmodellen gebruiken. Vooral om de verkeerde redenen.

Als uw inhoudsmodel vol eigenschappen is die in &quot;Id&quot;beëindigen u waarschijnlijk niet behoorlijk leveraging de hiërarchie.

Het is waar dat sommige knooppunten gedurende hun gehele levenscyclus een stabiele identificatie nodig hebben. Veel minder dan je zou denken. mix:verwijzing verstrekt zulk een mechanisme dat in de bewaarplaats wordt ingebouwd, zodat is er echt geen behoefte om met een extra manier op een stabiele manier omhoog te komen om een knoop te identificeren.

Houd ook in mening dat de punten door weg kunnen worden geïdentificeerd, en aangezien &quot;symlinks&quot;voor de meeste gebruikers veel zinvoller dan hardlinks in een unix filesystem maken, een weg voor de meeste toepassingen een betekenis heeft om naar een doelknoop te verwijzen.

Belangrijker, is het **mengeling**:verwijzing die betekent dat het op een knoop op het punt in tijd kan worden toegepast wanneer u eigenlijk het moet van verwijzingen voorzien.

Dus laten wij zeggen enkel omdat u een knoop van type &quot;Document&quot;zou kunnen van verwijzingen voorzien betekent niet dat uw &quot;document&quot;nodetype zich van mengeling moet uitbreiden:verwijzing op een statische manier aangezien het aan om het even welke instantie van het &quot;Document&quot;dynamisch kan worden toegevoegd.

#### Voorbeeld {#example-7}

Gebruiken:

```xml
/content/myblog/posts/iphone_shipping/attachments/front.jpg
```

in plaats van:

```xml
[Blog]
-- blogId
-- author
[Post]
-- postId
-- blogId
-- title
-- text
-- date
[Attachment]
-- attachmentId
-- postId
-- filename
+ resource (nt:resource)
```

