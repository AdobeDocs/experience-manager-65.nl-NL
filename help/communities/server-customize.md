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

| **[Essentiële ⇐ functies](essentials.md)** | **[Aanpassing aan client-side bezig](client-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

## Java™ API&#39;s {#java-apis}

>[!NOTE]
>
>De pakketlocatie van de communautaire API&#39;s kan veranderen wanneer u een upgrade uitvoert van de ene grote release naar de volgende.

### Interface van SocialComponent {#socialcomponent-interface}

Sociale componenten zijn POJO&#39;s die een bron voor een AEM Communities-functie vertegenwoordigen. Idealiter vertegenwoordigt elke SocialComponent een specifiek resourceType met blootgestelde GETters die gegevens aan de cliënt verstrekken zodat wordt het middel nauwkeurig vertegenwoordigd. Alle bedrijfslogica en weergavelogica worden ingekapseld in de sociale component, inclusief de sessiegegevens van de bezoeker van de site, indien nodig.

De interface bepaalt een basisreeks GETters die noodzakelijk zijn om een middel te vertegenwoordigen. Belangrijk, bepaalt de interface Kaart&lt;string object=&quot;&quot;> getAsMap() en String toJSONString() methoden die nodig zijn om Handlebars-sjablonen te renderen en GET JSON-eindpunten voor bronnen beschikbaar te maken.

Alle klassen SocialComponent moeten de interface uitvoeren `com.adobe.cq.social.scf.SocialComponent`

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

Een handgreep van de OSGi-dienst wordt verkregen door een beroep te doen op `com.adobe.cq.social.scf.SocialComponentFactoryManager`

### HTTP API - POST-aanvragen {#http-api-post-requests}

#### PostOperation-klasse {#postoperation-class}

De eindpunten van de HTTP API-POST zijn PostOperation-klassen die worden gedefinieerd door de implementatie van de `SlingPostOperation` interface (pakket) `org.apache.sling.servlets.post`).

De `PostOperation` eindpuntimplementatiesets `sling.post.operation` op een waarde waarop de bewerking reageert. Alle POST-aanvragen waarvoor een parameter:operation is ingesteld op die waarde, worden gedelegeerd aan deze implementatieklasse.

De `PostOperation` roept de `SocialOperation` die de voor de bewerking vereiste handelingen uitvoert.

De `PostOperation` ontvangt het resultaat van de `SocialOperation` en retourneert de juiste reactie op de client.

#### SocialOperation-klasse {#socialoperation-class}

Elk `SocialOperation` Het eindpunt breidt de klasse AbstractSocialOperation uit en treedt de methode met voeten `performOperation()`. Deze methode voert alle handelingen uit die nodig zijn om de bewerking te voltooien en een `SocialOperationResult` of anders een `OperationException`. In dat geval wordt een HTTP-foutstatus met een bericht geretourneerd, indien beschikbaar, in plaats van de normale JSON-respons of HTTP-successtatuscode.

Uitbreiden `AbstractSocialOperation` de mogelijkheid biedt om `SocialComponents` om JSON-reacties te verzenden.

#### SocialOperationResult, klasse {#socialoperationresult-class}

De `SocialOperationResult` wordt geretourneerd als het resultaat van de `SocialOperation` en bestaat uit een `SocialComponent`, HTTP-statuscode en HTTP-statusbericht.

De `SocialComponent` vertegenwoordigt de bron die door de bewerking is beïnvloed.

Voor een bewerking Maken `SocialComponent` opgenomen in de `SocialOperationResult` vertegenwoordigt het middel en voor een verrichting van de Update, vertegenwoordigt het het middel dat door de verrichting werd veranderd. Nee `SocialComponent` wordt geretourneerd voor een verwijderbewerking.

De gebruikte HTTP-statuscodes voor succes zijn:

* 201 voor bewerkingen maken
* 200 voor updatebewerkingen
* 204 voor verwijderingsbewerkingen

#### OperationException, klasse {#operationexception-class}

An `OperationExcepton` wordt gegenereerd wanneer een bewerking wordt uitgevoerd als de aanvraag ongeldig is of als er een andere fout optreedt. Interne fouten, onjuiste parameterwaarden of onjuiste machtigingen. An `OperationException` bestaat uit een HTTP-statuscode en een foutbericht die aan de client worden geretourneerd als reactie op de `PostOperatoin`.

#### OperationService-klasse {#operationservice-class}

In het kader van de sociale component wordt aanbevolen dat de bedrijfslogica die verantwoordelijk is voor de uitvoering van de bewerking, niet wordt geïmplementeerd binnen de `SocialOperation` klasse, maar in plaats daarvan gedelegeerd aan de dienst OSGi. Het gebruiken van de dienst OSGi voor bedrijfslogica staat een toe `SocialComponent`, die door een `SocialOperation` eindpunt, dat met andere code moet worden geïntegreerd en verschillende toegepaste bedrijfslogica hebben.

Alles `OperationService` klassen uitbreiden `AbstractOperationService`, waardoor extra extensies kunnen worden toegestaan die kunnen worden gekoppeld aan de uitgevoerde bewerking. Elke verrichting in de dienst wordt vertegenwoordigd door `SocialOperation` klasse. De `OperationExtensions` klasse kan tijdens verrichtingsuitvoering worden aangehaald door de methodes te roepen

* `performBeforeActions()`

  Voorcontroles/voorbewerking en validaties zijn toegestaan
* `performAfterActions()`

  Hiermee kunt u bronnen verder bewerken of aangepaste gebeurtenissen, workflows enzovoort aanroepen.

#### OperationExtension-klasse {#operationextension-class}

De `OperationExtension` de klassen zijn douanestukken van code die in een verrichting kunnen worden ingespoten die voor aanpassing van verrichtingen toestaat om aan bedrijfsbehoeften te voldoen. De consumenten van de component kunnen dynamisch en oplopend functionaliteit toevoegen aan de component. Met het extensie-/haakpatroon kunnen ontwikkelaars zich uitsluitend richten op de extensies zelf. Bovendien is het overbodig om volledige bewerkingen en componenten te kopiëren en te overschrijven.

## Voorbeeldcode {#sample-code}

Voorbeeldcode is beschikbaar in het dialoogvenster [Adobe Experience Cloud GitHub](https://github.com/Adobe-Marketing-Cloud) opslagplaats. Zoeken naar projecten met `aem-communities` of `aem-scf`.

## Aanbevolen procedures {#best-practices}

De weergave [Codeerrichtlijnen](code-guide.md) voor verschillende coderingsrichtlijnen en aanbevolen procedures voor AEM Communities-ontwikkelaars.

Zie ook [Storage Resource Provider (SRP) voor UGC](srp.md) voor meer informatie over het benaderen van door de gebruiker gegenereerde inhoud.

| **[Essentiële ⇐ functies](essentials.md)** | **[Aanpassing aan client-side bezig](client-customize.md)** |
|---|---|
|   | **[SCF Handlebars Helpers](handlebars-helpers.md)** |
