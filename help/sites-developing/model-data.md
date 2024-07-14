---
title: Gegevensmodellering - David Nuescheler's model
description: Aanbevelingen van David Nuescheler voor het modelleren van inhoud
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 6ce6a204-db59-4ed2-8383-00c6afba82b4
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1775'
ht-degree: 0%

---

# Gegevensmodellering - David Nuescheler&#39;s model{#data-modeling-david-nuescheler-s-model}

## Source {#source}

De volgende details zijn ideeën en opmerkingen van David Nuescheler.

David was mede-oprichter en CTO of Day Software AG, een toonaangevende leverancier van software voor contentbeheer en contentinfrastructuur, die in 2010 door Adobe werd aangeschaft. David is nu mede en VP van de Technologie van de Onderneming bij Adobe en leidt ook de ontwikkeling van JSR-170, de toepassing van de Opslagplaats van de Inhoud van Java™ (JCR) programmeringsinterface (API), de technologienorm voor inhoudsbeheer.

De verdere updates kunnen ook op [ https://cwiki.apache.org/confluence/display/jackrabbit/DavidsModel ](https://cwiki.apache.org/confluence/display/jackrabbit/DavidsModel) worden gezien.

## Inleiding van David {#introduction-from-david}

In verschillende discussies heb ik kunnen vaststellen dat ontwikkelaars enigszins ongerust zijn over de functies en functies die het JCR heeft voorgesteld bij het modelleren van content. Er is nog geen gids en weinig ervaring met het modelleren van inhoud in een opslagplaats en waarom het ene inhoudsmodel beter is dan het andere.

Terwijl in de relationele wereld, heeft de softwareindustrie ervaring op hoe te om gegevens te modelleren, is het nog in de vroege stadia voor de ruimte van de inhoudsbewaarplaats.

Ik zou willen beginnen deze leemte op te vullen door mijn mening te geven over de manier waarop de inhoud moet worden gemodelleerd. Ik hoop dat dit op een dag kan uitmonden in iets zinvoller voor de ontwikkelaarsgemeenschap, wat niet alleen &quot;mijn mening&quot; is, maar iets dat meer algemeen toepasbaar is. Denk eraan dat dit mijn eerste stap is.

>[!NOTE]
>
>Disclaimer: Deze richtsnoeren geven mijn persoonlijke, soms controversiële standpunten weer. Ik verheug mij erop deze richtsnoeren te bespreken en te verfijnen.

## Zeven eenvoudige regels {#seven-simple-rules}

### Regel 1: Gegevens eerst, structuur later. Misschien. {#rule-data-first-structure-later-maybe}

#### Toelichting {#explanation-1}

Ik raad aan om me geen zorgen te maken over een gedeclareerde gegevensstructuur in ERD-zin. Aanvankelijk.

Leer om van nt te houden:ongestructureerde (&amp; vrienden) in ontwikkeling.

Mijn bodemlijn: Structuur is duur en vaak is het helemaal niet nodig om structuur aan de onderliggende opslag uitdrukkelijk te verklaren.

Er is een impliciet contract met betrekking tot de structuur die uw toepassing inherent gebruikt. Stel dat ik de wijzigingsdatum van een blogbericht opsla in een lastModified-eigenschap. Mijn App weet automatisch om de wijzigingsdatum van dat zelfde bezit opnieuw te lezen, is er echt geen behoefte om dat uitdrukkelijk te verklaren.

Verdere gegevensbeperkingen zoals verplichte beperkingen of type- en waardebeperkingen mogen alleen worden toegepast wanneer dit om redenen van gegevensintegriteit vereist is.

#### Voorbeeld {#example-1}

Het bovenstaande voorbeeld van het gebruik van een eigenschap `lastModified` Date voor bijvoorbeeld het knooppunt &quot;blogbericht&quot;, betekent niet echt dat er behoefte is aan een speciaal knooppunttype. Ik zou `nt:unstructured` zeker in eerste instantie gebruiken voor mijn blogberichtknooppunten. Omdat ik in mijn blogtoepassing alleen maar de laatste wijzigingsdatum ga weergeven (mogelijk &#39;bestellen door&#39;), kan het me nauwelijks schelen of het een Date is. Omdat ik impliciet vertrouw op mijn blogtoepassing om toch een &quot;datum&quot;te zetten, is het echt niet nodig om de aanwezigheid van een `lastModified` datum in de vorm van een knooptype te verklaren.

### Regel 2: Bestel de inhoudshiërarchie. Laat dit niet gebeuren. {#rule-drive-the-content-hierarchy-don-t-let-it-happen}

#### Toelichting {#explanation-2}

De inhoudshiërarchie is een waardevol element. Laat het niet gebeuren; ontwerp het. Als u geen &quot;goede&quot;, mens-leesbare naam voor een knoop hebt, is dat waarschijnlijk iets dat u zou moeten heroverwegen. Willekeurige getallen zijn nauwelijks een &quot;goede naam&quot;.

Hoewel het gemakkelijk kan zijn om een bestaand relationeel model in een hiërarchisch model snel te zetten, zou men één of andere overweging in dat proces moeten zetten.

In mijn ervaring, als men van toegangscontrole en insluiting als goede bestuurders voor de inhoudshiërarchie denkt. Beschouw het als uw bestandssysteem. Gebruik zelfs bestanden en mappen om deze op uw lokale schijf te modelleren.

Persoonlijk, verkies ik hiërarchische overeenkomsten over het knoop die systeem aanvankelijk typt, en introduceer later het typen.

>[!CAUTION]
>
>De manier waarop een opslagplaats voor inhoud gestructureerd is, kan ook van invloed zijn op de prestaties. Voor de beste prestaties, zou het aantal kindknopen in bijlage aan individuele knopen in een inhoudsbewaarplaats niet 1&#39;000 moeten overschrijden.
>
>Zie [ hoeveel gegevens CRX behandelen?](https://helpx.adobe.com/experience-manager/kb/CrxLimitation.html)

#### Voorbeeld {#example-2}

Ik zou een eenvoudig blogsysteem als volgt modelleren. Aanvankelijk, geef ik zelfs niet om de respectieve knooptypes die ik op dit punt gebruik.

```xml
/content/myblog
/content/myblog/posts
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping

/content/myblog/comments/iphone_shipping/i_like_it_too
/content/myblog/comments/iphone_shipping/i_like_it_too/i_hate_it
```

Ik denk dat een van de dingen die duidelijk wordt, is dat de structuur van de inhoud gebaseerd is op het voorbeeld zonder verdere uitleg.

Wat in eerste instantie onverwachts kan zijn, is waarom ik de &quot;opmerkingen&quot; niet met de &quot;post&quot; zou opslaan, die te wijten is aan toegangscontrole die ik op een redelijk hiërarchische manier zou willen toepassen.

Met behulp van het bovenstaande inhoudsmodel kan ik de &quot;anonieme&quot; gebruiker gemakkelijk toestaan om opmerkingen te maken, maar de anonieme gebruiker op een alleen-lezen basis voor de rest van de werkruimte houden.

### Regel 3: De werkruimten zijn voor clone (), merge (), en update (). {#rule-workspaces-are-for-clone-merge-and-update}

#### Toelichting {#explanation-3}

Als u de methoden `clone()` , `merge()` of `update()` niet gebruikt in uw toepassing, kunt u waarschijnlijk slechts één werkruimte gebruiken.

&quot;Overeenkomende knooppunten&quot; is een concept dat is gedefinieerd in de specificatie JCR. In principe worden knooppunten die dezelfde inhoud vertegenwoordigen, in verschillende zogenaamde werkruimten samengevoegd.

Het JCR introduceert het abstracte concept Workspaces, dat veel ontwikkelaars onduidelijk laat wat te doen met hen. Ik zou willen voorstellen om uw gebruik van werkruimten als volgt te testen.

Als u een aanzienlijke overlapping van &quot;overeenkomstige&quot;knopen (hoofdzakelijk de knopen met zelfde UUID) in veelvoudige werkruimten hebt, zet u waarschijnlijk werkruimten aan goed gebruik.

Als knooppunten niet overlappen met dezelfde UUID, maakt u waarschijnlijk misbruik van werkruimten.

Gebruik geen werkruimten voor toegangsbeheer. Zichtbaarheid van inhoud voor een bepaalde groep gebruikers is geen goed argument om dingen in verschillende werkruimten te scheiden. JCR heeft &#39;Toegangsbeheer&#39; in de opslagplaats voor inhoud om dat mogelijk te maken.

De werkruimten zijn de grenzen voor verwijzingen en vragen.

#### Voorbeeld {#example-3}

Werkruimten gebruiken voor bijvoorbeeld:

* v1.2 van uw project vs. a v1.3 van uw project
* een &quot;ontwikkeling&quot;, &quot;kwaliteitscontrole&quot; en een &quot;gepubliceerde&quot; inhoudsstatus

Gebruik geen werkruimten voor bijvoorbeeld:

* thuismappen van gebruiker
* duidelijke inhoud voor verschillende doelgroepen, zoals publiek, privé, lokaal, ...
* postvakken voor verschillende gebruikers

### Regel 4: Let op de broers en zussen van dezelfde naam. {#rule-beware-of-same-name-siblings}

#### Toelichting {#explanation-4}

De Siblings van de zelfde Naam (SNS) is geïntroduceerd in de specificatie om verenigbaarheid met gegevensstructuren toe te staan die voor en uitgedrukt door XML worden ontworpen en, daarom waardevol voor JCR zijn. Nochtans, komt SNS met overheadkosten en ingewikkeldheid voor de bewaarplaats.

Om het even welk weg in de inhoudsbewaarplaats die SNS in één van zijn wegsegmenten bevat wordt veel minder stabiel. Als SNS wordt verwijderd of opnieuw in orde gebracht, heeft het een effect op de wegen van alle andere SNS en hun kinderen.

Voor de invoer van XML of interactie met bestaande XML, kan SNS noodzakelijk en nuttig zijn, maar ik heb nooit SNS (en ben nooit van plan) in mijn &quot;groene gebied&quot;gegevensmodellen gebruikt.

#### Voorbeeld {#example-4}

Gebruiken

```xml
/content/myblog/posts/what_i_learned_today
/content/myblog/posts/iphone_shipping
```

In plaats van

```xml
/content/blog[1]/post[1]
/content/blog[1]/post[2]
```

### Regel 5: Verwijzingen worden als schadelijk beschouwd. {#rule-references-considered-harmful}

#### Toelichting {#explanation-5}

Referenties impliceren referentiële integriteit. Het is belangrijk te begrijpen dat verwijzingen niet alleen extra kosten voor de bewaarplaats toevoegen die de referentiële integriteit beheren, maar ook uit een oogpunt van inhoudflexibiliteit duur zijn.

Persoonlijk, gebruik ik slechts verwijzingen wanneer ik echt geen gevaarlijke verwijzing kan behandelen en anders een weg, een naam, of een koord UUID gebruiken om naar een andere knoop te verwijzen.

#### Voorbeeld {#example-5}

Laten we aannemen dat ik &quot;verwijzingen&quot; van een document (a) naar een ander document (b) toestaat. Als ik deze relatie modelleer met behulp van referentie-eigenschappen, betekent dit dat de twee documenten zijn gekoppeld op het niveau van de gegevensopslagruimte. Ik kan document (a) niet afzonderlijk exporteren/importeren, omdat het doel van de referentie-eigenschap mogelijk niet bestaat. Andere bewerkingen, zoals samenvoegen, bijwerken, herstellen of klonen, worden ook beïnvloed.

Dus ik zou deze verwijzingen modelleren als &quot;zwakke verwijzingen&quot; (in JCR v1.0 komt dit in feite neer op tekenreekseigenschappen die de uuid van het doelknooppunt bevatten) of eenvoudig een pad gebruiken. Soms is het pad zinvoller om mee te beginnen.

Ik denk dat er gevallen zijn waarin een systeem echt niet werkt als een verwijzing gevaarlijk is, maar ik kan niet met een goed &quot;echt&quot; maar eenvoudig voorbeeld komen uit mijn directe ervaring.

### Regel 6: Bestanden zijn bestanden. {#rule-files-are-files}

#### Toelichting {#explanation-6}

Als een inhoudsmodel iets blootstelt dat zelfs ver als een dossier of een omslag ruikt, probeer ik te gebruiken (of zich uit) `nt:file`, `nt:folder`, en `nt:resource` uit te breiden.

In mijn ervaring, staan vele generische toepassingen interactie met nt:omslag en niet:dossiers impliciet toe en weten hoe te om die gebeurtenissen te behandelen en te tonen als zij met extra meta-informatie worden verrijkt. Bijvoorbeeld, wordt een directe interactie met de implementaties van de dossierserver zoals CIF of WebDAV die bovenop JCR zitten impliciet.

Ik denk dat als goede duimregel het volgende kan worden gebruikt: als u de bestandsnaam en het mime-type moet opslaan, is `nt:file`/ `nt:resource` een goede overeenkomst. Als u meerdere &quot;bestanden&quot; zou kunnen hebben, is de map nt:een goede plaats om deze op te slaan.

Als u meta-informatie voor uw middel moet toevoegen, laten wij zeggen &quot;auteur&quot;of een &quot;beschrijving&quot;bezit, breid `nt:resource` niet `nt:file` uit. Ik breid &#39;nt:file&#39; zelden uit en breid `nt:resource` vaak uit.

#### Voorbeeld {#example-6}

Stel dat iemand een afbeelding naar een blogbericht wil uploaden op:

```xml
/content/myblog/posts/iphone_shipping
```

Misschien zou de eerste darmreactie zijn om een binaire eigenschap toe te voegen die het beeld bevat.

Terwijl er goede gebruiksgevallen voor enkel het gebruiken van een binair bezit zijn (laten we zeggen is de naam irrelevant en mime-type impliciet is), in dit geval, adviseer ik de volgende structuur voor mijn blogvoorbeeld.

```xml
/content/myblog/posts/iphone_shipping/attachments [nt:folder]
/content/myblog/posts/iphone_shipping/attachments/front.jpg [nt:file]
/content/myblog/posts/iphone_shipping/attachments/front.jpg/jcr:content [nt:resource]
```

### Regel 7: Id&#39;s zijn slecht. {#rule-ids-are-evil}

#### Toelichting {#explanation-7}

In relationele databases zijn id&#39;s een noodzakelijk middel om relaties tot uitdrukking te brengen, zodat mensen ze ook in inhoudsmodellen gebruiken. Vooral om de verkeerde redenen.

Als uw inhoudsmodel vol eigenschappen is die in &quot;Id&quot;beëindigen, gebruikt u waarschijnlijk niet behoorlijk de hiërarchie.

Het is waar dat sommige knopen een stabiele identificatie door hun levende cyclus nodig hebben; minder dan u zou kunnen denken. Maar `mix:referenceable` heeft een dergelijk mechanisme dat in de repository is ingebouwd, dus het is niet nodig om met een extra manier te komen om een knooppunt op een stabiele manier te identificeren.

Houd er ook rekening mee dat items via het pad kunnen worden geïdentificeerd. En, zo veel als &quot;symlinks&quot;voor de meeste gebruikers veel redelijker dan harde verbindingen in een UNIX® filesystem maken, een weg voor de meeste toepassingen het nut om naar een doelknoop te verwijzen.

Belangrijker, is het **mengeling**:verwijzing wat betekent dat het op een knoop op het punt in tijd kan worden toegepast wanneer u het eigenlijk moet van verwijzingen voorzien.

Dus, alleen omdat u mogelijk wilt kunnen verwijzen naar een knooppunt van het type &quot;Document&quot;, betekent dit niet dat het knooppunttype &quot;Document&quot; moet worden uitgebreid van `mix:referenceable` op een statische manier. Dit komt omdat het dynamisch aan om het even welke instantie van het &quot;Document&quot;kan worden toegevoegd.

#### Voorbeeld {#example-7}

Gebruik:

```xml
/content/myblog/posts/iphone_shipping/attachments/front.jpg
```

In plaats van:

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
