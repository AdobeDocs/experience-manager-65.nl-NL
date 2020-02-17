---
title: Aanpassing op de server
seo-title: Aanpassing op de server
description: Server-kant aanpassen in AEM-gemeenschappen
seo-description: Server-kant aanpassen in AEM-gemeenschappen
uuid: 5e9bc6bf-69dc-414c-a4bd-74a104d7bd8f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: df5416ec-5c63-481b-99ed-9e5a91df2432
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Aanpassing op de server {#server-side-customization}

| **[Essentiële ⇐](essentials.md)** | **[Aanpassing aan clientzijde☐](client-customize.md)** |
|---|---|
|  | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

## Java API&#39;s {#java-apis}

>[!NOTE]
>
>De pakketlocatie van de communautaire API&#39;s kan veranderen wanneer u een upgrade uitvoert van de ene grote release naar de volgende.

### Interface van SocialComponent {#socialcomponent-interface}

SocialComponents zijn POJO&#39;s die een bron voor een AEM Communities-functie vertegenwoordigen. Idealiter vertegenwoordigt elke SocialComponent een specifiek resourceType met blootgestelde GETters die gegevens aan de cliënt verstrekken zodat wordt het middel nauwkeurig vertegenwoordigd. Alle bedrijfslogica en meningslogica wordt ingekapseld in SocialComponent, met inbegrip van de zittingsinformatie van de plaatsbezoeker, indien nodig.

De interface bepaalt een basisreeks GETters die noodzakelijk zijn om een middel te vertegenwoordigen. Belangrijk, bepaalt de interface Map&lt;String, Object> getAsMap () en String toJSONString () methodes die noodzakelijk zijn om de malplaatjes van Handlebars terug te geven en GET JSON eindpunten voor middelen bloot te stellen.

Alle klassen SocialComponent moeten de interface uitvoeren `com.adobe.cq.social.scf.SocialComponent`

### Interface SocialCollectionComponent {#socialcollectioncomponent-interface}

De interface SocialCollectionComponent breidt de interface SocialComponent uit om middelen beter te vertegenwoordigen die inzamelingen van andere middelen zijn.

Alle klassen SocialCollectionComponent moeten de interface com.adobe.cq.social.scf.SocialCollectionComponent uitvoeren

### SocialComponentFactory-interface {#socialcomponentfactory-interface}

Een SocialComponentFactory (factory) registreert een SocialComponent met het framework. De fabriek biedt een manier om het framework te laten weten welke sociale componenten beschikbaar zijn voor een bepaald resourceType en hun prioriteitsrangschikking&amp;ast; wanneer er meerdere sociale componenten zijn geïdentificeerd.

Een SocialComponentFactory is verantwoordelijk voor het creëren van een geval van geselecteerde SocialComponent die het mogelijk maakt om alle gebiedsdelen te injecteren nodig door SocialComponent van de fabriek gebruikend DI praktijken.

Een SocialComponentFactory is de dienst OSGi en heeft toegang tot andere diensten OSGi die tot SocialComponent door een aannemer kunnen worden overgegaan.

Alle klassen SocialComponentFactory moeten de interface implementeren `com.adobe.cq.social.scf.SocialComponentFactory`

Een implementatie van de methode SocialComponentFactory.getPriority() moet de hoogste waarde retourneren voordat de factory voor het opgegeven resourceType wordt gebruikt, zoals geretourneerd door getResourceType().

### SocialComponentFactoryManager-interface {#socialcomponentfactorymanager-interface}

De SocialComponentFactoryManager (manager) beheert alle sociale componenten die bij het framework zijn geregistreerd en is verantwoordelijk voor het selecteren van de SocialComponentFactory die voor een bepaalde resource (resourceType) moet worden gebruikt. Als geen fabrieken voor een specifieke resourceType worden geregistreerd, zal de manager een fabriek met het meest dichtbijgelegen super type voor de bepaalde middel terugkeren.

Een SocialComponentFactoryManager is de dienst OSGi en heeft toegang tot andere diensten OSGi die tot SocialComponent door een aannemer kunnen worden overgegaan.

Een handgreep van de OSGi-dienst wordt verkregen door een beroep te doen op `com.adobe.cq.social.scf.SocialComponentFactoryManager`

### HTTP-API - POST-aanvragen {#http-api-post-requests}

#### PostOperation-klasse {#postoperation-class}

De POST-eindpunten van de HTTP API zijn PostOperation-klassen die worden gedefinieerd door de `SlingPostOperation`interface (pakket `org.apache.sling.servlets.post`) te implementeren.

De `PostOperation`eindpuntimplementatie wordt ingesteld `sling.post.operation`op een waarde waarop de bewerking zal reageren. Alle POST-aanvragen met een parameter:operation die op die waarde is ingesteld, worden gedelegeerd aan deze implementatieklasse.

De `PostOperation`activeert de instantie `SocialOperation`die de handelingen uitvoert die nodig zijn voor de bewerking.

De `PostOperation`ontvanger ontvangt het resultaat van de `SocialOperation`en geeft de juiste reactie op de client.

#### Klasse SocialOperation {#socialoperation-class}

Elk `SocialOperation`eindpunt breidt de klasse AbstractSocialOperation uit en treedt de methode met voeten `performOperation().`Deze methode voert alle acties uit nodig om de verrichting te voltooien en terug te keren `SocialOperationResult`of anders een fout te werpen `OperationException`, in welk geval een de foutenstatus van HTTP met een bericht, indien beschikbaar, in plaats van de normale JSON reactie of de statuscode van succesHTTP is teruggekeerd.

Door de uitbreiding `AbstractSocialOperation`kunnen JSON-reacties opnieuw `SocialComponents`worden verzonden.

#### SocialOperationResult, klasse {#socialoperationresult-class}

De `SocialOperationResult`klasse wordt geretourneerd als het resultaat van de bewerking `SocialOperation`en bestaat uit een `SocialComponent`, HTTP-statuscode en HTTP-statusbericht.

Het `SocialComponent`vertegenwoordigt de bron die door de bewerking is beïnvloed.

Voor een Create verrichting, vertegenwoordigt `SocialComponent``SocialOperationResult`inbegrepen in het net gecreeerd middel en voor een verrichting van de Update, vertegenwoordigt het het middel dat door de verrichting werd veranderd. Er `SocialComponent`wordt geen bewerking geretourneerd voor Verwijderen.

De gebruikte HTTP-statuscodes voor succesmeldingen zijn:

* 201 voor bewerkingen maken
* 200 voor updatebewerkingen
* 204 voor verwijderingsbewerkingen

#### OperationException, klasse {#operationexception-class}

Er `OperationExcepton`kan een fout optreden bij het uitvoeren van een bewerking als de aanvraag ongeldig is of als er zich een andere fout voordoet, zoals interne fouten, onjuiste parameterwaarden, onjuiste machtigingen enzovoort. Een `OperationException`bestaat uit een HTTP-statuscode en een foutbericht, die als reactie op het `PostOperatoin`bericht aan de client worden geretourneerd.

#### OperationService-klasse {#operationservice-class}

Het sociale componentenkader adviseert dat de bedrijfslogica verantwoordelijk voor het uitvoeren van de verrichting niet binnen de `SocialOperation`klasse wordt uitgevoerd, maar in plaats daarvan aan een dienst wordt gedelegeerd OSGi. Het gebruiken van de dienst OSGi voor bedrijfslogica staat een `SocialComponent`, op door een `SocialOperation`eindpunt wordt gehandeld, om met andere code worden geïntegreerd en verschillende toegepaste bedrijfslogica hebben.

Alle `OperationService`klassen worden uitgebreid `AbstractOperationService`en er zijn extra extensies mogelijk die kunnen worden gekoppeld aan de bewerking die wordt uitgevoerd. Elke verrichting in de dienst wordt vertegenwoordigd door een `SocialOperation`klasse. De `OperationExtensions`klasse kan tijdens verrichtingsuitvoering worden aangehaald door de methodes te roepen

* `performBeforeActions()`
Voorcontroles/voorbewerking en validaties zijn toegestaan
* `performAfterActions()`
Staat voor verdere wijziging van middelen toe of het aanhalen van douanegebeurtenissen, werkschema&#39;s, enz.

#### OperationExtension-klasse {#operationextension-class}

`OperationExtension`de klassen zijn douanestukken van code die in een verrichting kunnen worden ingespoten die voor aanpassing van verrichtingen toestaat om aan bedrijfsbehoeften te voldoen. De consumenten van de component kunnen dynamisch en oplopend functionaliteit toevoegen aan de component. Met het extensie-/haakpatroon kunnen ontwikkelaars zich uitsluitend richten op de extensies zelf en is het overbodig volledige bewerkingen en componenten te kopiëren en te overschrijven.

## Voorbeeldcode {#sample-code}

Voorbeeldcode is beschikbaar in de [Adobe Marketing Cloud GitHub](https://github.com/Adobe-Marketing-Cloud) -opslagplaats. Zoek naar projecten die met of `aem-communities` of `aem-scf`.

## Aanbevolen werkwijzen {#best-practices}

Bekijk de sectie [Codeerrichtlijnen](code-guide.md) voor diverse codeerrichtlijnen en beste praktijken voor ontwikkelaars van AEM Communities.

Zie ook de Leverancier van het Middel van de [Opslag (SRP) voor UGC](srp.md) om over de toegang tot van gebruiker geproduceerde inhoud te leren.

| **[Essentiële ⇐](essentials.md)** | **[Aanpassing aan clientzijde☐](client-customize.md)** |
|---|---|
|  | **[SCF Handlebars Helpers](handlebars-helpers.md)** |

