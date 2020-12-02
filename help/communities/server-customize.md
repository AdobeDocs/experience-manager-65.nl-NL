---
title: Aanpassing op de server
seo-title: Aanpassing op de server
description: Server-kant aanpassen in AEM Communities
seo-description: Server-kant aanpassen in AEM Communities
uuid: 5e9bc6bf-69dc-414c-a4bd-74a104d7bd8f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: df5416ec-5c63-481b-99ed-9e5a91df2432
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---


# Aanpassing aan serverzijde {#server-side-customization}

| **[Essentiële ⇐](essentials.md)** | **[Aanpassing aan clientzijde☐](client-customize.md)** |
|---|---|
|  | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

## Java API&#39;s {#java-apis}

>[!NOTE]
>
>De pakketlocatie van de communautaire API&#39;s kan veranderen wanneer u een upgrade uitvoert van de ene grote release naar de volgende.

### Interface van sociale component {#socialcomponent-interface}

Sociale componenten zijn POJO&#39;s die een bron voor een AEM Communities-functie vertegenwoordigen. Idealiter vertegenwoordigt elke SocialComponent een specifiek resourceType met blootgestelde GETters die gegevens aan de cliënt verstrekken zodat wordt het middel nauwkeurig vertegenwoordigd. Alle bedrijfslogica en meningslogica wordt ingekapseld in SocialComponent, met inbegrip van de zittingsinformatie van de plaatsbezoeker, indien nodig.

De interface bepaalt een basisreeks GETters die noodzakelijk zijn om een middel te vertegenwoordigen. Belangrijk, bepaalt de interface Map&lt;String, Object> getAsMap () en String toJSONString () methodes die noodzakelijk zijn om de malplaatjes van Handlebars terug te geven en GET JSON eindpunten voor middelen bloot te stellen.

Alle klassen SocialComponent moeten de interface `com.adobe.cq.social.scf.SocialComponent` uitvoeren

### Interface SocialCollectionComponent {#socialcollectioncomponent-interface}

De interface SocialCollectionComponent breidt de interface SocialComponent uit om middelen beter te vertegenwoordigen die inzamelingen van andere middelen zijn.

Alle klassen SocialCollectionComponent moeten de interface com.adobe.cq.social.scf.SocialCollectionComponent uitvoeren

### SocialComponentFactory Interface {#socialcomponentfactory-interface}

Een SocialComponentFactory (factory) registreert een SocialComponent met het framework. De fabriek verstrekt een manier om het kader te laten weten welke SocialComponents voor een bepaalde resourceType en hun prioritaire rangschikking beschikbaar zijn wanneer veelvoudige SocialComponents worden geïdentificeerd.

Een SocialComponentFactory is verantwoordelijk voor het creëren van een geval van geselecteerde SocialComponent die het mogelijk maakt om alle gebiedsdelen te injecteren nodig door SocialComponent van de fabriek gebruikend DI praktijken.

Een SocialComponentFactory is de dienst OSGi en heeft toegang tot andere diensten OSGi die tot SocialComponent door een aannemer kunnen worden overgegaan.

Alle klassen SocialComponentFactory moeten de interface `com.adobe.cq.social.scf.SocialComponentFactory` uitvoeren

Een implementatie van de methode SocialComponentFactory.getPriority() moet de hoogste waarde retourneren voordat de factory voor het opgegeven resourceType wordt gebruikt, zoals geretourneerd door getResourceType().

### SocialComponentFactoryManager-interface {#socialcomponentfactorymanager-interface}

De SocialComponentFactoryManager (manager) beheert alle sociale componenten die bij het framework zijn geregistreerd en is verantwoordelijk voor het selecteren van de SocialComponentFactory die voor een bepaalde resource (resourceType) moet worden gebruikt. Als geen fabrieken voor een specifieke resourceType worden geregistreerd, zal de manager een fabriek met het meest dichtbijgelegen super type voor de bepaalde middel terugkeren.

Een SocialComponentFactoryManager is de dienst OSGi en heeft toegang tot andere diensten OSGi die tot SocialComponent door een aannemer kunnen worden overgegaan.

Een greep van de OSGi-service wordt verkregen door `com.adobe.cq.social.scf.SocialComponentFactoryManager` aan te roepen

### HTTP API - POST vraagt {#http-api-post-requests}

#### PostOperation-klasse {#postoperation-class}

De eindpunten van de HTTP API-POST zijn PostOperation-klassen die worden gedefinieerd door de `SlingPostOperation`-interface (package `org.apache.sling.servlets.post`) te implementeren.

De `PostOperation` eindpuntimplementatie plaatst `sling.post.operation` aan een waarde waarop de verrichting zal antwoorden. Alle verzoeken van de POST met een:parameter van de verrichting die aan die waarde wordt geplaatst zullen aan deze implementatieklasse worden gedelegeerd.

`PostOperation` roept `SocialOperation` aan die de acties noodzakelijk voor de verrichting uitvoert.

De `PostOperation` ontvangt het resultaat van `SocialOperation` en retourneert de juiste reactie op de client.

#### Klasse SocialOperation {#socialoperation-class}

Elk `SocialOperation` eindpunt breidt de klasse AbstractSocialOperation uit en treedt de methode `performOperation()` met voeten. Deze methode voert alle acties uit die nodig zijn om de bewerking te voltooien en een `SocialOperationResult` te retourneren of anders een `OperationException` te genereren. In dat geval wordt een HTTP-foutstatus met een bericht geretourneerd, indien beschikbaar, in plaats van de normale JSON-respons of HTTP-statuscode van succes.

Als u `AbstractSocialOperation` uitbreidt, kunt u `SocialComponents` opnieuw gebruiken om JSON-reacties te verzenden.

#### SocialOperationResult-klasse {#socialoperationresult-class}

De klasse `SocialOperationResult` wordt geretourneerd als het resultaat van de `SocialOperation` en bestaat uit een `SocialComponent`, HTTP-statuscode en HTTP-statusbericht.

De `SocialComponent` vertegenwoordigt de bron die door de bewerking is beïnvloed.

Voor een Create verrichting, `SocialComponent` inbegrepen in `SocialOperationResult` vertegenwoordigt het middel enkel gecreeerd en voor een verrichting van de Update, vertegenwoordigt het de middel die door de verrichting werd veranderd. Er wordt geen `SocialComponent` geretourneerd voor een verwijderbewerking.

De gebruikte HTTP-statuscodes voor succes zijn:

* 201 voor bewerkingen maken
* 200 voor updatebewerkingen
* 204 voor verwijderingsbewerkingen

#### OperationException-klasse {#operationexception-class}

Een `OperationExcepton` kan worden gegenereerd wanneer een bewerking wordt uitgevoerd als de aanvraag ongeldig is of als er een andere fout optreedt, zoals interne fouten, onjuiste parameterwaarden, onjuiste machtigingen, enz. Een `OperationException` bestaat uit een HTTP-statuscode en een foutbericht die als reactie op de `PostOperatoin` aan de client worden geretourneerd.

#### OperationService-klasse {#operationservice-class}

Het sociale componentenkader adviseert dat de bedrijfslogica verantwoordelijk voor het uitvoeren van de verrichting niet binnen de `SocialOperation` klasse wordt uitgevoerd, maar in plaats daarvan aan een dienst wordt gedelegeerd OSGi. Het gebruiken van de dienst OSGi voor bedrijfslogica staat een `SocialComponent` toe, die op door een `SocialOperation` eindpunt wordt gehandeld, om met andere code worden geïntegreerd en verschillende bedrijfslogica hebben toegepast.

Alle `OperationService` klassen breiden `AbstractOperationService` uit, toelatend extra uitbreidingen die in de verrichting kunnen aansluiten die wordt uitgevoerd. Elke bewerking in de service wordt vertegenwoordigd door een klasse `SocialOperation`. De klasse `OperationExtensions` kan tijdens verrichtingsuitvoering worden aangehaald door de methodes te roepen

* `performBeforeActions()`

   Voorcontroles/voorbewerking en validaties zijn toegestaan
* `performAfterActions()`

   Staat voor verdere wijziging van middelen toe of het aanhalen van douanegebeurtenissen, werkschema&#39;s, enz.

#### OperationExtension-klasse {#operationextension-class}

`OperationExtension` de klassen zijn douanestukken van code die in een verrichting kunnen worden ingespoten die voor aanpassing van verrichtingen toestaat om aan bedrijfsbehoeften te voldoen. De consumenten van de component kunnen dynamisch en oplopend functionaliteit toevoegen aan de component. Met het extensie-/haakpatroon kunnen ontwikkelaars zich uitsluitend richten op de extensies zelf. Bovendien is het overbodig om volledige bewerkingen en componenten te kopiëren en te overschrijven.

## Voorbeeldcode {#sample-code}

De code van de steekproef is beschikbaar in [Adobe Marketing Cloud GitHub](https://github.com/Adobe-Marketing-Cloud) bewaarplaats. Zoek naar projecten die met of `aem-communities` of `aem-scf` vooraf zijn.

## Best practices voor {#best-practices}

Bekijk de sectie [Coderingsrichtlijnen](code-guide.md) voor verschillende codeerrichtlijnen en aanbevolen procedures voor AEM Communities-ontwikkelaars.

Zie ook [Storage Resource Provider (SRP) voor UGC](srp.md) voor meer informatie over de toegang tot door de gebruiker gegenereerde inhoud.

| **[Essentiële ⇐](essentials.md)** | **[Aanpassing aan clientzijde☐](client-customize.md)** |
|---|---|
|  | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

