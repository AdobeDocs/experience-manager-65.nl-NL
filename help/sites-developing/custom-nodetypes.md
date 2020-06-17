---
title: Aangepaste knooppunttypen
seo-title: Aangepaste knooppunttypen
description: AEM is gebaseerd op Sling en gebruikt een JCR-opslagplaats met knooppunttypen die door beide worden aangeboden, maar AEM biedt ook een reeks aangepaste knooppunttypen
seo-description: AEM is gebaseerd op Sling en gebruikt een JCR-opslagplaats met knooppunttypen die door beide worden aangeboden, maar AEM biedt ook een reeks aangepaste knooppunttypen
uuid: f2022504-e433-4b42-9cc1-eef41086483a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: aae186eb-e059-4a9d-b02d-86a86c86589d
translation-type: tm+mt
source-git-commit: 07eb53f19cf7c7c2799c95ba9df54f4673d72fdc
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 7%

---


# Aangepaste knooppunttypen{#custom-node-types}

Omdat AEM op het Verkopen gebaseerd is en een bewaarplaats JCR gebruikt, zijn de knooptypes die door beide worden aangeboden beschikbaar voor gebruik:

* [JCR-knooppunttypen](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Sling Node Types](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

Daar komt nog bij. AEM biedt een reeks aangepaste knooppunttypen.

## Audit {#audit}

### cq:AuditEvent {#cq-auditevent}

**Beschrijving**

Bepaalt het knooptype van een knoop van de controlegebeurtenis.

* `@prop cq:time`
* `@prop cq:userid`
* `@prop cq:path`
* `@prop cq:type`
* `@prop cq:category`
* `@prop cq:properties`

**Definitie**

* `[cq:AuditEvent]`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ * (nt:base) = nt:base multiple version`
* `- cq:time (date)`
* `- cq:userid (string)`
* `- cq:path (string)`
* `- cq:type (string)`
* `- cq:category (string)`
* `- cq:properties (binary)`

## Opmerking {#comment}

### cq:opmerking {#cq-comment}

**Beschrijving**

Definieert het notatietype van een opmerkingsknooppunt.

* `@prop userIdentifier`

**Definitie**

* `[cq:Comment] > mix:title, mix:created, mix:language, nt:unstructured, cq:Taggable`
* `- email (string)`
* `- ip (string)`
* `- referer (string)`
* `- url (string)`
* `- userAgent (string)`
* `- userIdentifier (string)`
* `- authorizableId (string)`

### cq:CommentAttachment {#cq-commentattachment}

**Beschrijving**

Definieert het notatietype van een `commentattachment` knooppunt

**Definitie**

* `[cq:CommentAttachment] > nt:file`
   * `- * (undefined)`
   * `- * (undefined) multiple`

### cq:CommentContent {#cq-commentcontent}

**Beschrijving**

Definieert het notatietype van een commentaarinhoudsknooppunt

**Definitie**

* `[cq:Comment] > mix:title, mix:created, mix:language, nt:unstructured, cq:Taggable`
* `- email (string)`
* `- ip (string)`
* `- referer (string)`
* `- url (string)`
* `- userAgent (string)`
* `- userIdentifier (string)`
* `- authorizableId (string)`

### cq:GeoLocation {#cq-geolocation}

**Beschrijving**

Een mix die een geografische locatie in decimale graden (DD) definieert

* `@prop latitude` - breedte gecodeerd als dubbel in decimale graden
* `@prop longitude` - lengtegraad gecodeerd als dubbel in decimale graden

**Definitie**

* `[cq:GeoLocation] mixin`
* `- latitude (double)`
* `- longitude (double)`

### cq:Trackback {#cq-trackback}

**Beschrijving**

Definieert het knooptype van een trackback-knooppunt.

**Definitie**

* `[cq:Trackback] > mix:title, mix:created, mix:language, nt:unstructured`

## Kern {#core}

### cq:pagina {#cq-page}

**Beschrijving**

Definieert de standaard CQ-pagina.

* `@node jcr:content` - Primaire inhoud van de pagina.

**Definitie**

* `[cq:Page] > nt:hierarchyNode orderable`
   * `+ jcr:content (nt:base) = nt:unstructured copy primary`
   * `+ * (nt:base) = nt:base version`

### cq:PseudoPage {#cq-pseudopage}

**Beschrijving**

Definieert een mixinetype dat knooppunten markeert als pseudopagina&#39;s. Dit betekent dat ze kunnen worden aangepast voor ondersteuning voor pagina- en WCM-bewerkingen.

**Definitie**

* `[cq:PseudoPage] mixin`

### cq:PageContent {#cq-pagecontent}

**Beschrijving**

Definieert het standaardknooppunt voor pagina-inhoud, met de minimale eigenschappen die door WCM worden gebruikt.

* `@prop jcr:title` - Titel voor de pagina.
* `@prop jcr:description` - Beschrijving van deze pagina.
* `@prop cq:template` - Pad naar de sjabloon die is gebruikt om de pagina te maken.
* `@prop cq:allowedTemplates` - Lijst met reguliere expressies die worden gebruikt om het pad of de paden naar de toegestane sjabloon te bepalen.
* `@prop pageTitle` - Titel wordt meestal weergegeven in de `<title>` tag.
* `@prop navTitle` - Titel wordt meestal gebruikt in de navigatie.
* `@prop hideInNav` - Geeft aan of de pagina moet worden verborgen in de navigatie.
* `@prop onTime` - Tijdstip waarop deze pagina geldig wordt.
* `@prop offTime` - Tijd waarop deze pagina ongeldig wordt.
* `@prop cq:lastModified` - Datum waarop de pagina (of de bijbehorende alinea&#39;s) voor het laatst is gewijzigd.
* `@prop cq:lastModifiedBy` - Laatste gebruiker om de pagina (of de alinea&#39;s) te wijzigen.
* `@prop jcr:language` - De taal van de pagina-inhoud.

>[!NOTE]
>
>Het gebruik van dit type is niet verplicht voor pagina-inhoud.

**Definitie**
* `[cq:PageContent] > nt:unstructured, mix:title, mix:created, cq:OwnerTaggable, sling:VanityPath, cq:ReplicationStatus, sling:Resource orderable`
   * `- cq:template (string)`
   * `- cq:allowedTemplates (string) multiple`
   * `- pageTitle (string)`
   * `- navTitle (string)`
   * `- hideInNav (boolean)`
   * `- onTime (date)`
   * `- offTime (date)`
   * `- cq:lastModified (date)`
   * `- cq:lastModifiedBy (string)`
   * `- cq:designPath (string)`
   * `- jcr:language (string)`

### cq:sjabloon {#cq-template}

**Beschrijving**

Definieert een CQ-sjabloon.

* `@node jcr:content` - Standaardinhoud voor nieuwe pagina&#39;s.
* `@node icon.png` - Een bestand dat een kenmerkend pictogram bevat.
* `@node thumbnail.png` - Een bestand dat een kenmerkende miniatuurafbeelding bevat.
* `@node workflows` - Workflowconfiguratie automatisch toewijzen. De configuratie volgt de onderstaande structuur:
   * `+ workflows`
      * `+ name1`
         * `- cq:path`
            * `- cq:workflowName`
* `@prop allowedParents` - Reguliere-expressiepatronen om te bepalen welke paden naar sjablonen zijn toegestaan als bovenliggende sjablonen.
* `@prop allowedChildren` - Reguliere-expressiepatronen om te bepalen welke paden naar sjablonen zijn toegestaan als onderliggende sjablonen.
* `@prop ranking` - Positie in de lijst met sjablonen in het dialoogvenster Pagina maken.

**Definitie**

* `[cq:Template] > nt:hierarchyNode, mix:title`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ * (nt:base) = nt:base multiple version`
   * `+ jcr:content (nt:base) copy`
   * `+ icon.png (nt:file) copy`
   * `+ thumbnail.png (nt:file) copy`
   * `+ workflows (nt:base) copy`
   * `- allowedParents (string) multiple`
   * `- allowedChildren (string) multiple`
   * `- ranking (long)`

### cq:Component {#cq-component}

**Beschrijving**

Definieert een CQ-component.

* `@prop jcr:title` - Titel voor de component.
* `@prop jcr:description` - Beschrijving van het onderdeel.
* `@node dialog` - Primair dialoogvenster.
* `@prop dialogPath` - Primair dialoogvenster (alternatief voor dialoogvenster).
* `@node design_dialog` - Het dialoogvenster Ontwerpen.
* `@prop cq:cellName` - Naam van de ontwerpcel.
* `@prop cq:isContainer` - Geeft aan of dit een containercomponent is. Hierdoor worden de celnamen van onderliggende componenten in plaats van padnamen gebruikt. Het `parsys` is bijvoorbeeld een containercomponent. Als deze waarde niet is gedefinieerd, wordt de controle uitgevoerd op basis van het bestaan van een `cq:childEditConfig`.
* `@prop cq:noDecoration` - Indien waar (true), worden er geen decoratietags `div` getekend wanneer deze component wordt opgenomen.
* `@node cq:editConfig` - De configuratie die de parameters voor de bewerkbalk definieert.
* `@node cq:childEditConfig` - De bewerkingsconfiguratie die wordt overgeërfd door onderliggende componenten.
* `@node cq:htmlTag` - Definieert aanvullende tagkenmerken die worden toegevoegd aan de tag &quot;omringend&quot; `div` wanneer de component wordt opgenomen.
* `@node icon.png`- Een bestand dat een kenmerkend pictogram bevat.
* `@node thumbnail.png` - Een bestand dat een kenmerkende miniatuurafbeelding bevat.
* `@prop allowedParents` - Reguliere-expressiepatronen om het pad of de paden te bepalen van componenten die zijn toegestaan als bovenliggende componenten.
* `@prop allowedChildren` - Reguliere-expressiepatronen om het pad of de paden te bepalen van componenten die zijn toegestaan als onderliggende componenten.
* `@node virtual` - Bevat subknooppunten die virtuele componenten weerspiegelen die worden gebruikt voor het slepen en neerzetten van de component.
* `@prop componentGroup` - Naam van de componentgroep die wordt gebruikt voor slepen en neerzetten van de component.
* `@node cq:infoProviders` - Bevat subknooppunten, die elk een bezit hebben `className` dat naar een `PageInfoProvider`verwijst.

**Definitie**

* `[cq:Component] > nt:folder, mix:title, sling:ResourceSuperType`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ * (nt:base) = nt:base multiple version`
   * `+ dialog (nt:base) = nt:unstructured copy`
   * `- dialogPath (string)`
   * `+ design_dialog (nt:base) = nt:unstructured copy`
   * `- cq:cellName (string)`
   * `- cq:isContainer (boolean)`
   * `- cq:noDecoration (boolean)`
   * `+ cq:editConfig (cq:EditConfig) = cq:EditConfig copy`
   * `+ cq:childEditConfig (cq:EditConfig) = cq:EditConfig copy`
   * `+ cq:htmlTag (nt:base) = nt:unstructured copy`
   * `+ icon.png (nt:file) copy`
   * `+ thumbnail.png (nt:file) copy`
   * `- allowedParents (string) multiple`
   * `- allowedChildren (string) multiple`
   * `+ virtual (nt:base) = sling:Folder copy`
   * `- componentGroup (string)`
   * `+ cq:infoProviders (nt:base) = nt:unstructured copy`

### cq:ComponentMixin {#cq-componentmixin}

**Beschrijving**

Definieert een CQ-component als mixinetype.

**Definitie**

`[cq:ComponentMixin] > cq:Component mixin`

### cq:EditConfig {#cq-editconfig}

**Beschrijving**

Definieert de configuratie voor de &quot;editbar&quot;.

* `@prop cq:dialogMode` - Modus van het dialoogvenster:
   * `floating` - voor een normaal zwevend dialoogvenster
   * `inline` - inline bewerken
   * `auto` - automatische detectie (afhankelijk van de beschikbare ruimte)
* `@node cq:inplaceEditing` - Voer de bewerkingsconfiguratie voor deze component in.
* `@prop cq:layout`- Lay-out van de bewerkbalk:
   * `editbar` - bewerkbalk
   * `rollover` - rollover-frame
   * `auto` - automatische detectie
* `@node cq:formParameters`- Aanvullende parameters die moeten worden toegevoegd aan het dialoogvenster.
* `@prop cq:actions`- Lijst met handelingen (knoppen op de bewerkbalk of menu-items).
* `@node cq:actionConfigs` - Widgetconfiguraties voor bewerkbalk- of menu-items.
* `@prop cq:emptyText` - Tekst die moet worden weergegeven als er geen visuele inhoud aanwezig is.
* `@node cq:dropTargets` - Verzameling van `{@link cq:DropTargetConfig}` knooppunten.

**Definitie**

* `[cq:EditConfig] > nt:unstructured, nt:hierarchyNode orderable`
   * `- cq:dialogMode (string) < 'auto', 'floating', 'inline'`
   * `- cq:layout (string) < 'editbar', 'rollover', 'auto' + cq:formParameters (nt:base) = nt:unstructured`
   * `- cq:actions (string) multiple`
   * `+ cq:actionConfigs (nt:base) = nt:unstructured`
   * `- cq:emptyText (string)`
   * `+ cq:dropTargets (nt:base) = nt:unstructured`
   * `+ cq:listeners (nt:base) = cq:EditListenersConfig`

### cq:DropTargetConfig {#cq-droptargetconfig}

**Beschrijving**

Vormt één dalingsdoel van een component. De naam van dit knooppunt wordt gebruikt als een id voor slepen en neerzetten.

* `@prop accept` - Lijst van MIME-typen die door deze neerzetbestemming worden geaccepteerd; bijv. `["image/*"]`
* `@prop groups` - Lijst met slepen- en neerzetgroepen die een bron accepteren.
* `@prop propertyName` - Naam van de eigenschap die wordt gebruikt om de verwijzing op te slaan.

**Definitie**

* `[cq:DropTargetConfig] > nt:unstructured orderable`
   * `- accept (string) multiple`
   * `- groups (string) multiple`
   * `- propertyName (string)`
   * `+ parameters (nt:base) = nt:unstructured`

### cq:VirtualComponent {#cq-virtualcomponent}

**Beschrijving**

Definieert een virtuele CQ-component. Deze worden momenteel alleen gebruikt voor de nieuwe wizard voor slepen en neerzetten van componenten.

* `@prop jcr:title` - Titel van deze component.
* `@prop jcr:description` - Beschrijving van dit onderdeel.
* `@node cq:editConfig` - Configuratie bewerken die de parameters voor de bewerkbalk definieert.
* `@node cq:childEditConfig`- Configuratie bewerken die wordt overgeërfd door onderliggende componenten.
* `@node icon.png` - Een bestand dat een kenmerkend pictogram bevat.
* `@node thumbnail.png` - Een bestand dat een kenmerkende miniatuurafbeelding bevat.
* `@prop allowedParents` - Reguliere-expressiepatronen om het pad of de paden te bepalen van componenten die zijn toegestaan als bovenliggende componenten.
* `@prop allowedChildren` - Reguliere-expressiepatronen om het pad of de paden te bepalen van componenten die zijn toegestaan als onderliggende componenten.
* `@prop componentGroup` - Naam van de componentgroep voor het slepen en neerzetten van de component.

**Definitie**

`[cq:VirtualComponent] > nt:folder, mix:title`
`- * (undefined)`
`- * (undefined) multiple`
`+ * (nt:base) = nt:base multiple version`
`+ cq:editConfig (cq:EditConfig) = cq:EditConfig copy`
`+ icon.png (nt:file) copy`
`+ thumbnail.png (nt:file) copy`
`- allowedParents (string) multiple`
`- allowedChildren (string) multiple`
`- componentGroup (string)`

### cq:EditListenersConfig {#cq-editlistenersconfig}

**Beschrijving**

Definieert de (client)listeners die moeten worden uitgevoerd op een bewerkingsgebeurtenis. De waarden moeten verwijzen naar een geldige clientlistenerfunctie of een vooraf gedefinieerde sneltoets bevatten:

* `REFRESH_PAGE`
* `REFRESH_SELF`
* `REFRESH_PARENT`

* `@prop aftercreate` - Wordt geactiveerd nadat een component is gemaakt.
* `@prop afteredit` - Wordt geactiveerd nadat een component is bewerkt (gewijzigd).
* `@prop afterdelete` - Wordt geactiveerd nadat een component is verwijderd.
* `@prop afterinsert` - Wordt geactiveerd nadat een component aan deze container is toegevoegd.
* `@prop afterremove` - Wordt geactiveerd nadat een component uit deze container is verwijderd.
* `@prop aftermove` - Wordt geactiveerd nadat componenten in deze container zijn verplaatst.

**Definitie**

* `[cq:EditListenersConfig]`
   * `- &ast; (undefined)`
   * `- &ast; (undefined) multiple`
   * `+ &ast; (nt:base) = nt:base multiple version`
   * `- aftercreate (string)`
   * `- afteredit (string)`
   * `- afterdelete (string)`
   * `- afterinsert (string)`
   * `- afterremove (string)`
   * `- aftermove (string)`

## DAM {#dam}

### dam:AssetContent {#dam-assetcontent}

**Beschrijving**

Inhoud van een DAM-element.

**Definitie**

* `[dam:AssetContent] > nt:unstructured`
   * `+ metadata (nt:unstructured)`
   * `+ renditions (nt:folder)`

### dam:Asset {#dam-asset}

**Beschrijving**

DAM-middelen.

**Definitie**

`[dam:Asset] > nt:hierarchyNode`
`+ jcr:content (dam:AssetContent) = dam:AssetContent copy primary`
`+ * (nt:base) = nt:base version`

### dam:Miniatuur {#dam-thumbnail}

**Beschrijving**

Miniatuur die een DAM-element vertegenwoordigt.

**Definitie**

* `[dam:Thumbnails]`
   * `mixin`
   * `+ dam:thumbnails (nt:folder)`

## Containerlijst voor levering {#delivery-container-list}

### cq:containerList {#cq-containerlist}

**Beschrijving**

Containerlijst.

**Definitie**

* `[cq:containerList]`
   * `mixin`

## Afleveringspagina {#delivery-page}

### cq:Cq4PageAttributes {#cq-cq-pageattributes}

**Beschrijving**

`cq:attributes` is het knooppunttype voor de ContentBus versietags. Dit knooppunt heeft alleen een reeks eigenschappen; waarvan er drie vooraf zijn gedefinieerd: &quot;created&quot;, &quot;csd&quot; en &quot;timestampe&quot;.

* `@prop created (long) mandatory copy` - Tijdstempel voor het maken van de versiegegevens, meestal het tijdstip van controle van de vorige versie of het tijdstip van het maken van de pagina.
* `@prop csd (string) mandatory copy` - csd, standaardkenmerk, kopie van de eigenschap cq:csd van het paginaknooppunt
* `@prop timestamp (long) mandatory copy` - Tijdstempel van laatste versiewijziging, meestal controletijd.
* `@prop * (string) copy` - Aanvullende kenmerken, versieingesteld met het bovenliggende knooppunt.

**Definitie**

* `[cq:Cq4PageAttributes] > nt:base`
   * `- created (long) mandatory copy`
   * `- csd (string) mandatory copy`
   * `- timestamp (long) mandatory copy`
   * `- &ast; (string) copy`

### cq:Cq4ContentPage {#cq-cq-contentpage}

**Beschrijving**

Het knooppunttype `cq:contentPage` bevat de bezit en kindknoopdefinities voor ContentBus inhoudspagina&#39;s. Alleen wanneer dit mixintype wordt toegevoegd aan een knooppunt van het type `cq:page`, wordt een knooppunt een ContentBus-inhoudspagina.

De items in a `cq:Cq4ContentPage` zijn:

* `@prop cq:csd` - De ContentBus-CSD van de pagina.
* `@node cq:content` - De inhoud van de pagina. Dit onderliggende knooppunt bestaat niet als het paginaknooppunt de status &quot;Bestaande zonder inhoud&quot; of &quot;Verwijderd&quot; heeft.
* `@node cq:attributes` - De lijst met paginakenmerken, die voorheen versietags werden genoemd. Dit knooppunt is verplicht voor het type cq:contentPage. Het attributenknooppunt is versioned, wanneer het paginaknooppunt is versioned.

**Definitie**

* `[cq:Cq4ContentPage]`
   * `- cq:csd (string) mandatory copy`
   * `+ cq:attributes (cq:Cq4PageAttributes)`

## Importeur {#importer}

### cq:PollConfig {#cq-pollconfig}

**Beschrijving**

Opiniepeilingconfiguratie.

* `@prop source (String) mandatory` - Data source URI, this is required and must not empty
* `@prop target (String)` - De doellocatie waar gegevens die uit de gegevensbron zijn opgehaald, worden opgeslagen. Dit is optioneel en wordt standaard ingesteld op het knooppunt cq:PollConfig.
* `@prop interval (Long)` - Het interval in seconden waarmee naar nieuwe of bijgewerkte gegevens van de gegevensbron wordt gezocht. Dit is optioneel en wordt standaard ingesteld op 30 minuten (1800 seconden).
* [Aangepaste services voor het importeren van gegevens maken voor Adobe Experience Manager](https://helpx.adobe.com/experience-manager/using/polling.html)

**Definitie**

* `[cq:PollConfig]
   * `mixin`
   * `- source (String) mandatory`
   * `- target (String)`
   * `- interval (Long)`

### cq:PollConfigFolder {#cq-pollconfigfolder}

**Beschrijving**

Het primaire knooppunttype van gemak om opiniepeilingsknopen gemakkelijk tot stand te brengen.

**Definitie**

`[cq:PollConfigFolder] > sling:Folder, cq:PollConfig`

## Locatie {#location}

### cq:GeoLocation {#cq-geolocation-1}

**Beschrijving**

Een mix die een geografische locatie in decimale graden (DD) definieert.

* `@prop latitude` - De breedte is gecodeerd als twee decimale graden.
* `@prop longitude` - Lengtegraad gecodeerd als dubbel in decimale graden.

**Definitie**

* `[cq:GeoLocation]
   * `mixin`
   * `- latitude (double)`
   * `- longitude (double)`

## Mailer {#mailer}

### cq:mailerMessage {#cq-mailermessage}

**Beschrijving**

MailerService nodetypes. De mailer gebruikt knopen die deze mixin als wortelknopen van berichtdefinities hebben.

**Definitie**

* `[cq:mailerMessage]`
   * `mixin`
   * `- messageStatus (string)`
   * `= 'new'`
   * `mandatory autocreated`

## MSM {#msm}

### cq:LiveRelationship {#cq-liverelationship}

**Beschrijving**

Definieert een LiveRelationship-mix. Een primair bronknooppunt (Besturingselement) en een live copy-knooppunt (gecontroleerd) kunnen via een LiveRelationship praktisch worden gekoppeld.

**Definitie**

* `[cq:LiveRelationship] mixin`
   * `- cq:lastRolledout (date)`
   * `- cq:lastRolledoutBy (string)`
   * `- cq:sourceUUID (string)`

### cq:LiveSync {#cq-livesync}

**Beschrijving**

Definieert een LiveSync-mix. Als een knooppunt betrokken is bij een LiveRelationship met een primair bronknooppunt (Besturend) en een live-knooppunt (gecontroleerd), wordt dit gemarkeerd als een LiveSync.

* `@prop cq:master` - Pad van de primaire bron (besturing) van de LiveRelationship.
* `@prop cq:isDeep` - Definieert of de relatie beschikbaar is voor kinderen.
* `@prop cq:syncTrigger` - Definieert wanneer de synchronisatie wordt geactiveerd.
* `@node * LiveSyncAction` - Acties die synchroon moeten worden uitgevoerd

**Definitie**

`[cq:LiveSync] > cq:LiveRelationship mixin orderable`
`+ * (cq:LiveSyncAction) = cq:LiveSyncAction`
`+ cq:LiveSyncConfig (nt:base) = cq:LiveSyncConfig`

### cq:LiveSyncCanceled {#cq-livesynccancelled}

**Beschrijving**

Definieert een LiveSyncCanceled-mix. Annuleer het gedrag LiveSync van een live copy (gecontroleerd) knooppunt dat mogelijk betrokken is bij een LiveRelationship vanwege een van de bovenliggende knooppunten.

* `@prop cq:isCancelledForChildren` - Hiermee wordt gedefinieerd of een LiveSync wordt geannuleerd. ook voor kinderen.

**Definitie**

* `[cq:LiveSyncCancelled] > cq:LiveRelationship mixin`
   * `- cq:isCancelledForChildren (boolean)`

### cq:LiveSyncAction {#cq-livesyncaction}

**Beschrijving**

Definieert een LiveSyncAction die aan een LiveSync is gekoppeld.

* `@prop name` - Naam van handeling
* `@prop value` - Waarde van handeling

**Definitie**

* `[cq:LiveSyncAction] > nt:unstructured`

### cq:LiveSyncConfig {#cq-livesyncconfig}

**Beschrijving**

Configuratie van live synchronisatie.

**Definitie**

* `[cq:LiveSyncConfig]`
   * `- cq:master (string) mandatory`
   * `- cq:isDeep (boolean)`
   * `- cq:trigger (string) /** deprecated **/`

Voeg voor AEM 5.4 aan het einde van de lijst toe:

* `- cq:rolloutConfigs (string) multiple /** deprecated **/`

### cq:BluepintAction {#cq-blueprintaction}

**Beschrijving**

Blauwdruk, actie

**Definitie**

* `[cq:BlueprintAction] > nt:unstructured`

## Platform {#platform}

### cq:Console {#cq-console}

**Beschrijving**

Definieert het knooptype van een consoleknooppunt.

**Definitie**

* `[cq:Console] > sling:VanityPath, mix:title`
   * `mixin`

## Replicatie {#replication}

### cq:ReplicationStatus {#cq-replicationstatus}

**Beschrijving**

Bepaalt de informatie van de replicatiestatus mixin.

* `@prop cq:lastPublished`- De datum waarop de pagina voor het laatst is gepubliceerd (niet meer gebruikt).
* `@prop cq:lastPublishedBy`- De gebruiker die de pagina als laatste heeft gepubliceerd (niet meer gebruikt).
* `@prop cq:lastReplicated` - De datum waarop de pagina voor het laatst is gerepliceerd.
* `@prop cq:lastReplicatedBy` - De gebruiker die de pagina als laatste heeft gerepliceerd.
* `@prop cq:lastReplicationAction` - De replicatieactie: activeren of deactiveren.
* `@prop cq:lastReplicationStatus` - De replicatiestatus (niet meer gebruikt).

**Definitie**

* `[cq:ReplicationStatus]
   * `mixin`
   * `- cq:lastPublished (date) ignore`
   * `- cq:lastPublishedBy (string) ignore`
   * `- cq:lastReplicated (date) ignore`
   * `- cq:lastReplicatedBy (string) ignore`
   * `- cq:lastReplicationAction (string) ignore`
   * `- cq:lastReplicationStatus (string) ignore`

## Beveiliging {#security}

### cq:ApplicationPrivilege {#cq-applicationprivilege}

**Beschrijving**

Definieert een toepassingsbevoegdheid.

**Definitie**

* `[cq:ApplicationPrivilege] mixin`

### cq:PrivilegeAcl {#cq-privilegeacl}

**Beschrijving**

Bepaalt toepassingsvoorrecht ACL.

* `@prop cq:isPathDependent`
* `@node * ACEs`

**Definitie**

* `[cq:PrivilegeAcl] > cq:ApplicationPrivilege mixin orderable`
   * `- cq:isPathDependent (boolean)`
   * `+ * (cq:PrivilegeAce) = cq:PrivilegeAce`

### cq:PrivilegeAce {#cq-privilegeace}

**Beschrijving**

Bepaalt een toepassingsvoorrecht ACE.

* `@prop path`
* `@prop deny`

**Definitie**

* `[cq:PrivilegeAce]`
   * `- path mandatory`
   * `- deny (boolean)`

### cq:ApplicationPrivilege {#cq-applicationprivilege-1}

**Beschrijving**

Definieert een toepassingsbevoegdheid.

**Definitie**

* `[cq:ApplicationPrivilege] mixin`

### cq:PrivilegeAcl {#cq-privilegeacl-1}

**Beschrijving**

Bepaalt toepassingsvoorrecht ACL.

* `@prop cq:isPathDependent`
* `@node * ACEs`

**Definitie**

* `[cq:PrivilegeAcl] > cq:ApplicationPrivilege mixin orderable`
   * `- cq:isPathDependent (boolean)`
   * `+ * (cq:PrivilegeAce) = cq:PrivilegeAce`

### cq:PrivilegeAce {#cq-privilegeace-1}

**Beschrijving**

Bepaalt een toepassingsvoorrecht ACE.

* `@prop path`
* `@prop deny`

**Definitie**

* `[cq:PrivilegeAce]`
   * `- path mandatory`
   * `- deny (boolean)`

## Site-importmodule {#site-importer}

### cq:ComponentExtractorSource {#cq-componentextractorsource}

**Beschrijving**

Definieert een mixinetype dat bestanden markeert die kunnen worden geopend met de componentextractor.

**Definitie**

`[cq:ComponentExtractorSource] mixin`

## Tags {#tagging}

### cq:Tag {#cq-tag}

**Beschrijving**

Definieert één tag, maar kan ook tags bevatten, waardoor een taxonomie ontstaat

**Definitie**

* `[cq:Tag] > nt:base, mix:title`
   * `- sling:resourceType (String)`
   * `- * (undefined) multiple`
   * `- * (undefined)`
   * `+ * (nt:base) = cq:Tag version`

### cq:Tagable {#cq-taggable}

**Beschrijving**

Abstract basismengsel voor controleerbare inhoud.

* `@node cq:tags`

**Definitie**

* `[cq:Taggable]`
   * `- cq:tags (string) multiple`

### cq:OwnerTaggable {#cq-ownertaggable}

**Beschrijving**

Alleen auteurs/eigenaars mogen de inhoud labelen (gemodereerd/beheerd coderen).

**Definitie**

* `[cq:OwnerTaggable] > cq:Taggable`

### cq:UserTaggable {#cq-usertaggable}

**Beschrijving**

Elke gebruiker/openbare website kan de inhoud (Web2.0-stijl) labelen die wordt gebruikt in cq:userContent.

**Definitie**

* `[cq:UserTaggable] > cq:Taggable`
   * `mixin`

### cq:AllowsUserContent {#cq-allowsusercontent}

**Beschrijving**

Voegt een `cq:userContent` subknooppunt toe dat door gebruikers kan worden gewijzigd. Elke gebruiker zal zijn eigen `cq:userContent/<userid>` subnode hebben, die typisch de mixin heeft `cq:UserTaggable`.

**Definitie**

* `[cq:AllowsUserContent]`
   * `mixin`
   * `+ cq:userContent (nt:unstructured)`

Uitgebreide variant, die de `cq:userContent` boom explicieter bepaalt

* `[cq:AllowsUserContent]`
   * `mixin`
   * `+ cq:userContent (cq:UserContent)`

### cq:UserContent {#cq-usercontent}

**Beschrijving**

Kan door gebruikers worden gewijzigd.

**Definitie**

* `[cq:UserContent] > nt:unstructured`
   * `// userids`
   * `+ * (cq:UserData)`
   * `// other content`
   * `+ * (nt:base)`

### cq:UserData {#cq-userdata}

**Beschrijving**

Gebruikersgegevens

**Definitie**

* `[cq:UserData] > nt:unstructured, cq:UserTaggable`

## Widgets {#widgets}

### cq:ClientLibraryFolder {#cq-clientlibraryfolder}

**Beschrijving**

Map voor clientbibliotheek

**Definitie**

* `[cq:ClientLibraryFolder] > sling:Folder`
   * `- categories (string) multiple`
   * `- dependencies (string) multiple`

### cq:Widget {#cq-widget}

**Beschrijving**

Widget

**Definitie**

* `[cq:Widget] > nt:unstructured orderable`
   * `- xtype (string)`
   * `- name (string)`
   * `- title (string)`
   * `+ items (nt:base) = cq:WidgetCollection copy`

### cq:WidgetCollection {#cq-widgetcollection}

**Beschrijving**

Widget-verzameling

**Definitie**

* `[cq:WidgetCollection] > nt:unstructured`
   * `orderable`
   * `+ * (cq:Widget) = cq:Widget copy`

### cq:Dialoogvenster {#cq-dialog}

**Beschrijving**

Dialoog

**Definitie**

* `[cq:Dialog] > cq:Widget orderable`

### cq:Panel {#cq-panel}

**Beschrijving**

Deelvenster

**Definitie**

`[cq:Panel] > cq:Widget orderable`

### cq:TabPanel {#cq-tabpanel}

**Beschrijving**

Deelvenster Tab

**Definitie**

* `[cq:TabPanel] > cq:Panel orderable&#39;
   * `- activeTab (long)`

### cq:Field {#cq-field}

**Beschrijving**

Veld

**Definitie**

* `[cq:Field] > cq:Widget orderable`
   * `- fieldLabel (string)`
   * `- value (string)`
   * `- ignoreData (boolean)`

## Wiki {#wiki}

### wiki:onderwerp {#wiki-topic}

**Beschrijving**

Wiki-onderwerp

**Definitie**

* `[wiki:Topic] > nt:unstructured, nt:hierarchyNode, mix:versionable, mix:lockable`
   * `+ * (wiki:Topic) version`
   * `+ wiki:attachments (nt:folder) = nt:folder version`
   * `+ wiki:properties (wiki:Properties) = wiki:Properties copy`
   * `- wiki:text (string) mandatory primary`
   * `- wiki:lastModified (date) mandatory`
   * `- wiki:lastModifiedBy (string) mandatory`
   * `- wiki:topicName`
   * `- wiki:topicTitle`
   * `- wiki:lockedBy`
   * `- wiki:logMessage (string)`
   * `- wiki:quietSave (boolean)`

### wiki:gebruiker {#wiki-user}

**Beschrijving**

Wiki-gebruiker

**Definitie**

* `[wiki:User] mixin`
   * `- wiki:subscriptions (string) multiple`

### wiki:eigenschappen {#wiki-properties}

**Beschrijving**

Wiki-eigenschappen

**Definitie**

* `[wiki:Properties]`
   * `- wiki:isGlobal (boolean)`
   * `- * (undefined)`

## Workflow {#workflow}

### cq:Workflow {#cq-workflow}

**Beschrijving**

Vertegenwoordigt een werkstroominstantie.

**Definitie**

* `[cq:Workflow] > nt:base, mix:referenceable`
   * `- modelId (String)`
   * `- modelVersion (String)`
   * `- startTime (Date)`
   * `- endTime (Date)`
   * `- initiator (String)`
   * `- &ast; (undefined)`
   * `- &ast; (undefined) multiple`
   * `- sling:resourceType (String) = "cq/workflow/components/instance" mandatory autocreated`
   * `+ workflowStack (nt:unstructured)`
   * `+ wait (nt:unstructured)`
   * `+ orTab (nt:unstructured)`
   * `+ data (cq:WorkflowData)`
   * `+ history (nt:unstructured)`
   * `+ metaData (nt:unstructured)`
   * `+ workItems (nt:unstructured)`

### cq:WorkItem {#cq-workitem}

**Beschrijving**

Werkitem.

**Definitie**

* `[cq:WorkItem]`
   * `- assignee (String)`
   * `- workflowId (String)`
   * `- nodeId (String)`
   * `- startTime (Date)`
   * `- endTime (Date)`
   * `- dueTime (Date)`
   * `- sling:resourceType (String) = "cq/workflow/components/workitem" mandatory autocreated`
   * `+ metaData (nt:unstructured)`

### cq:Payload {#cq-payload}

**Beschrijving**

Payload

**Definitie**

* `[cq:Payload]`
   * `- path (Path)`
   * `- uuid (String)`
   * `- jcr:url (String)`
   * `- binary (Binary)`
   * `- javaObject (String)`
   * `- * (undefined)`
   * `- * (undefined) multiple`

### cq:WorkflowData {#cq-workflowdata}

**Beschrijving**

Werkstroomgegevens

**Definitie**

* `[cq:WorkflowData]`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ payload (cq:Payload)`
   * `+ metaData (nt:unstructured) copy`

### cq:WorkflowModel {#cq-workflowmodel}

**Beschrijving**

Workflowconfiguratie automatisch toewijzen. De configuratie volgt onderstaande structuur:
* `workflows`
   * `+ name1`
      * `- cq:path`
      * `- cq:workflowName`
   * `+ workflows (nt:base)`

**Definitie**

* `[cq:WorkflowModel] > nt:base, mix:versionable`
   * `orderable`
   * `- title (String)`
   * `- description (String)`
   * `- sling:resourceType (String) = "cq/workflow/components/model" mandatory autocreated`
   * `+ nodes (nt:unstructured)`
      * `copy`
   * `+ transitions (nt:unstructured)`
      * `copy`
   * `+ metaData (nt:unstructured)`
      * `copy`

### cq:WorkflowNode {#cq-workflownode}

**Beschrijving**

Workflowknooppunt

**Definitie**

* `[cq:WorkflowNode] orderable`
   * `- title (String)`
   * `- description (String)`
   * `- maxIdleTime (long)`
   * `- type (String)`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ metaData (nt:unstructured)`
      * `copy`
   * `+ timeoutConfiguration (nt:unstructured)`
      * `copy`

### cq:WorkflowTransition {#cq-workflowtransition}

**Beschrijving**

Workflowovergang

**Definitie**

* `[cq:WorkflowTransition] orderable`
   * `- from (String)`
   * `- to (String)`
   * `- rule (String)`
   * `+ metaData (nt:unstructured)`
      * `copy`

### cq:OrTab {#cq-ortab}

**Beschrijving**

Of tabblad

**Definitie**

* `[cq:OrTab]`
   * `- workflowId (String) // not compulsory as this node will already be attached to the workflow node`
   * `- nodeId (String)`

### cq:wachten {#cq-wait}

**Beschrijving**

Wachten

**Definitie**

* `[cq:Wait]`
   * `- workflowId (String) // not compulsory as this node will be already attached to the workflow node`
   * `- destNodeId (String)`
   * `- fromNodeId (String)`

### cq:WorkflowStack {#cq-workflowstack}

**Beschrijving**

Workflowstack

**Definitie**

* `[cq:WorkflowStack]`
   * `- containeeInstanceId (String)`
   * `- parentInstanceId (String)`
   * `- nodeId (String)`

### cq:ProcessStack {#cq-processstack}

**Beschrijving**

Processtapel

**Definitie**

* `[cq:ProcessStack]`
   * `- workflowId (String) // not compulsory as this node will be already attached to the workflow node`
   * `- containerWorkflowModelId (String)`
   * `- containerWorkflowNodeId`
   * `- containerWorkflowEndNodeId // still needed (if name already defines that id)`

### cq:WorkflowLauncher {#cq-workflowlauncher}

**Beschrijving**

Workflow starten

**Definitie**

* `[cq:WorkflowLauncher]`
   * `- nodetype (String)`
   * `- glob (String)`
   * `- eventType (Long)`
   * `- description (String)`
   * `- condition (String)`
   * `- workflow (String)`
   * `- * (undefined)`
   * `- * (undefined) multiple`
