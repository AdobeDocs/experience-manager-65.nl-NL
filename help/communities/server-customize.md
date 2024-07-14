---
title: Aanpassing op de server
description: Leer hoe server-zijaanpassingen in de Gemeenschappen van Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 190735bc-1909-4b92-ba4f-a221c0cd5be7
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Aanpassing op de server {#server-side-customization}

| **[Essentiële elementen ⇐](essentials.md)** | **[Cliënt-kant Aanpassing](client-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

## Java™ API&#39;s {#java-apis}

>[!NOTE]
>
>De pakketlocatie van de communautaire API&#39;s kan veranderen wanneer u een upgrade uitvoert van de ene grote release naar de volgende.

### Interface van SocialComponent {#socialcomponent-interface}

Sociale componenten zijn POJO&#39;s die een bron voor een AEM Communities-functie vertegenwoordigen. Idealiter vertegenwoordigt elke SocialComponent een specifiek resourceType met blootgestelde GETters die gegevens aan de cliënt verstrekken zodat wordt het middel nauwkeurig vertegenwoordigd. Alle bedrijfslogica en weergavelogica worden ingekapseld in de sociale component, inclusief de sessiegegevens van de bezoeker van de site, indien nodig.

De interface bepaalt een basisreeks GETters die noodzakelijk zijn om een middel te vertegenwoordigen. Belangrijk, bepaalt de interface Map&lt;String, Object> getAsMap () en String toJSONString () methodes die noodzakelijk zijn om de malplaatjes van Handlebars terug te geven en GET JSON eindpunten voor middelen bloot te stellen.

Alle klassen SocialComponent moeten de interface implementeren `com.adobe.cq.social.scf.SocialComponent`

### Interface SocialCollectionComponent {#socialcollectioncomponent-interface}

De interface SocialCollectionComponent breidt de interface SocialComponent uit om middelen beter te vertegenwoordigen die inzamelingen van andere middelen zijn.

Alle klassen SocialCollectionComponent moeten de interface com.adobe.cq.social.scf.SocialCollectionComponent uitvoeren

### SocialComponentFactory-interface {#socialcomponentfactory-interface}

Een SocialComponentFactory (factory) registreert een SocialComponent met het framework. De fabriek verstrekt een manier om het kader te laten weten welke SocialComponents voor een bepaalde resourceType en hun prioritaire rangschikking beschikbaar zijn wanneer veelvoudige SocialComponents worden geïdentificeerd.

Een SocialComponentFactory is verantwoordelijk voor het creëren van een geval van geselecteerde SocialComponent die het mogelijk maakt om alle gebiedsdelen te injecteren nodig door SocialComponent van de fabriek gebruikend DI praktijken.

Een SocialComponentFactory is de dienst OSGi en heeft toegang tot andere diensten OSGi die tot SocialComponent door een aannemer kunnen worden overgegaan.

Alle klassen SocialComponentFactory moeten de interface implementeren `com.adobe.cq.social.scf.SocialComponentFactory`

Een implementatie van de methode SocialComponentFactory.getPriority() moet de hoogste waarde retourneren voor de factory die voor het opgegeven resourceType moet worden gebruikt, zoals geretourneerd door getResourceType().

### SocialComponentFactoryManager-interface {#socialcomponentfactorymanager-interface}

De SocialComponentFactoryManager (manager) beheert alle sociale componenten die bij het framework zijn geregistreerd en is verantwoordelijk voor het selecteren van de SocialComponentFactory die voor een bepaalde resource (resourceType) moet worden gebruikt. Als er geen fabrieken zijn geregistreerd voor een specifiek resourceType, retourneert de manager een fabriek met het dichtstbijzijnde supertype voor de opgegeven resource.

Een SocialComponentFactoryManager is de dienst OSGi en heeft toegang tot andere diensten OSGi die tot SocialComponent door een aannemer kunnen worden overgegaan.

Een greep van de OSGi-service wordt verkregen door het aanroepen van `com.adobe.cq.social.scf.SocialComponentFactoryManager`

### HTTP API - POST-aanvragen {#http-api-post-requests}

#### PostOperation-klasse {#postoperation-class}

De eindpunten van de HTTP API-POST zijn PostOperation-klassen die worden gedefinieerd door de `SlingPostOperation` interface (package `org.apache.sling.servlets.post` ) te implementeren.

De implementatie van het `PostOperation` eindpunt stelt `sling.post.operation` in op een waarde waarop de bewerking reageert. Alle POST-aanvragen waarvoor een parameter:operation is ingesteld op die waarde, worden gedelegeerd aan deze implementatieklasse.

`PostOperation` roept `SocialOperation` aan, die de handelingen uitvoert die nodig zijn voor de bewerking.

`PostOperation` ontvangt het resultaat van `SocialOperation` en retourneert de juiste reactie op de client.

#### SocialOperation-klasse {#socialoperation-class}

Elk `SocialOperation` eindpunt breidt de klasse AbstractSocialOperation uit en treedt de methode `performOperation()` met voeten. Deze methode voert alle handelingen uit die nodig zijn om de bewerking te voltooien en een `SocialOperationResult` retourneren of anders een `OperationException` genereren. In dat geval wordt een HTTP-foutstatus met een bericht geretourneerd, indien beschikbaar, in plaats van de normale JSON-respons of HTTP-successtatuscode.

Als u `AbstractSocialOperation` uitbreidt, kunt u `SocialComponents` opnieuw gebruiken om JSON-reacties te verzenden.

#### SocialOperationResult, klasse {#socialoperationresult-class}

De `SocialOperationResult` -klasse wordt geretourneerd als het resultaat van de `SocialOperation` -gebeurtenis en bestaat uit een `SocialComponent` -statuscode, HTTP-statuscode en HTTP-statusbericht.

De `SocialComponent` vertegenwoordigt de bron die door de bewerking is beïnvloed.

Voor een Create verrichting, `SocialComponent` inbegrepen in `SocialOperationResult` vertegenwoordigt het middel gecreeerd en voor een verrichting van de Update, vertegenwoordigt het de middel die door de verrichting werd veranderd. Er wordt geen `SocialComponent` geretourneerd voor een verwijderbewerking.

De gebruikte HTTP-statuscodes voor succes zijn:

* 201 voor bewerkingen maken
* 200 voor updatebewerkingen
* 204 voor verwijderingsbewerkingen

#### OperationException, klasse {#operationexception-class}

Een `OperationExcepton` wordt gegenereerd wanneer een bewerking wordt uitgevoerd als de aanvraag ongeldig is of als er een andere fout optreedt. Interne fouten, onjuiste parameterwaarden of onjuiste machtigingen. Een `OperationException` bestaat uit een HTTP-statuscode en een foutbericht die als reactie op de `PostOperatoin` aan de client worden geretourneerd.

#### OperationService-klasse {#operationservice-class}

Het framework voor sociale componenten raadt aan dat de bedrijfslogica die verantwoordelijk is voor het uitvoeren van de bewerking, niet wordt geïmplementeerd binnen de klasse `SocialOperation` , maar in plaats daarvan wordt gedelegeerd aan een OSGi-service. Het gebruiken van de dienst OSGi voor bedrijfslogica staat a `SocialComponent` toe, gehandeld door een `SocialOperation` eindpunt, om met andere code worden geïntegreerd en verschillende toegepaste bedrijfslogica hebben.

Alle `OperationService` -klassen breiden `AbstractOperationService` uit, waardoor extra extensies mogelijk worden toegevoegd aan de bewerking die wordt uitgevoerd. Elke bewerking in de service wordt vertegenwoordigd door een `SocialOperation` -klasse. De klasse `OperationExtensions` kan tijdens de uitvoering van de bewerking worden aangeroepen door de methoden aan te roepen

* `performBeforeActions()`

  Voorcontroles/voorbewerking en validaties zijn toegestaan
* `performAfterActions()`

  Hiermee kunt u bronnen verder bewerken of aangepaste gebeurtenissen, workflows enzovoort aanroepen.

#### OperationExtension-klasse {#operationextension-class}

De `OperationExtension` -klassen zijn aangepaste codefragmenten die in een bewerking kunnen worden geïnjecteerd en die het mogelijk maken bewerkingen aan te passen aan de zakelijke behoeften. De consumenten van de component kunnen dynamisch en oplopend functionaliteit toevoegen aan de component. Met het extensie-/haakpatroon kunnen ontwikkelaars zich uitsluitend richten op de extensies zelf. Bovendien is het overbodig om volledige bewerkingen en componenten te kopiëren en te overschrijven.

## Voorbeeldcode {#sample-code}

De code van de steekproef is beschikbaar in [ Adobe Experience Cloud GitHub ](https://github.com/Adobe-Marketing-Cloud) bewaarplaats. Zoek naar projecten die met `aem-communities` of `aem-scf` vooraf zijn bepaald.

## Aanbevolen procedures {#best-practices}

Bekijk de [ sectie van de Richtlijnen van de Codering ](code-guide.md) voor diverse coderingsrichtlijnen en beste praktijken voor de ontwikkelaars van AEM Communities.

Zie ook {de Leverancier van het Middel van 0} Opslag (SRP) voor UGC ](srp.md) om over de toegang tot van gebruiker geproduceerde inhoud te leren.[

| **[Essentiële elementen ⇐](essentials.md)** | **[Cliënt-kant Aanpassing](client-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers](handlebars-helpers.md)** |
