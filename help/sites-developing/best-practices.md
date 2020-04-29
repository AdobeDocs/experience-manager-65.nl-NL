---
title: Aanbevolen werkwijzen
seo-title: Aanbevolen werkwijzen
description: Adobe Engineering- en Consulting-teams hebben een uitgebreide reeks best practices ontwikkeld voor AEM-ontwikkelaars
seo-description: Adobe Engineering- en Consulting-teams hebben een uitgebreide reeks best practices ontwikkeld voor AEM-ontwikkelaars
uuid: f962c31f-8140-482f-b189-16376e23bfed
contentOwner: Justin Edelson
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 99678c1a-81f3-4fb3-bf73-98f0691c3fb6
translation-type: tm+mt
source-git-commit: e562939f1c64d8345b4c2a28e4b882200d9e4c07

---


# Best Practices{#best-practices}

## Aanbevolen procedures voor ontwikkelaars - Aan de slag {#best-practices-for-developers-getting-started}

Adobe Engineering- en Consulting-teams hebben een uitgebreide reeks aanbevolen procedures ontwikkeld voor AEM-ontwikkelaars. De ontwikkelaar van Adobe hanteert deze beste praktijken aangezien zij kernAEM productupdates en klantencode voor klantenimplementatie ontwikkelen.

Voordat u uw AEM-ontwikkelingsproject start, moet u eerst de volgende aanbevolen procedures doornemen:

* [Ontwikkelingspraktijken](/help/sites-developing/development-practices.md)
* [Inhoudsarchitectuur](/help/sites-developing/content-architecture.md)
* [Softwarearchitectuur](/help/sites-developing/software-architecture.md)
* [Codetips](/help/sites-developing/coding-tips.md)
* [Codepitten](/help/sites-developing/code-pitfalls.md)
* [JCR-interactie](/help/sites-developing/jcr-integration.md)
* [OSGi-bundels](/help/sites-developing/osgi-bundles.md)
* [Aanbevolen werkwijzen voor Java API](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

### Aanvullende informatie over aanbevolen procedures {#additional-best-practices-information}

Op de volgende gebieden is documentatie beschikbaar die specifiek is voor de ontwikkeling van beste praktijken:

* [Sites](#sites)
* [Gemeenschappen](/help/sites-developing/best-practices.md#communities)
* [Tooling/HTL](/help/sites-developing/best-practices.md#tooling-htl)

Specifieke documenten worden beschreven en gekoppeld aan de volgende tabellen.

Voor beste praktijken bij het beheren, het opstellen en het handhaven, of het ontwerpen, zie één van het volgende:

* [Aanbevolen werkwijzen beheren](/help/sites-administering/administer-best-practices.md)
* [Aanbevolen werkwijzen ontwerpen](/help/sites-authoring/best-practices.md)
* [Tips en trucs implementeren](/help/sites-deploying/best-practices.md)

## Sites {#sites}

Voor het beheren en ontwerpen van uw website-inhoud gelden enkele aanbevolen procedures die als volgt worden beschreven:

<table>
 <tbody>
  <tr>
   <td>Een deel van de theorie achter de standaard, aanraakinterface.</td>
   <td><p><a href="/help/sites-developing/touch-ui-concepts.md">Interface voor aanraakbediening: Concepten</a></p> <p><a href="/help/sites-developing/touch-ui-structure.md">Interface voor aanraakbediening: Structuur</a></p> </td>
   <td>Deze documenten bieden een overzicht van de concepten en structuur van de interface met aanraakbediening.</td>
  </tr>
  <tr>
   <td>Interface voor aanraakbediening: Consoles aanpassen </td>
   <td><a href="/help/sites-developing/customizing-consoles-touch.md">UI-consoles met aanraakbediening aanpassen</a></td>
   <td>In dit document wordt beschreven hoe u de consoles voor de interface met aanraakbediening het beste kunt uitbreiden.</td>
  </tr>
  <tr>
   <td>Interface met aanraakbediening: Het ontwerpen van pagina's aanpassen</td>
   <td><a href="/help/sites-developing/customizing-page-authoring-touch.md">UI-pagina's met aanraakbediening aanpassen</a></td>
   <td>Beschrijft hoe te om paginaontwerp voor aanraking-toegelaten UI uit te breiden.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td><a href="/help/sites-developing/workflows-best-practices.md">Workflows ontwikkelen en uitbreiden</a></td>
   <td><p>Met workflows kunt u activiteiten van Adobe Experience Manager (AEM) automatiseren en kunnen grote hoeveelheden van de verwerking in een AEM-omgeving worden uitgevoerd. Daarom wordt u ten zeerste aangeraden de implementaties van workflows zorgvuldig te plannen.</p> </td>
  </tr>
 </tbody>
</table>

## Gemeenschappen {#communities}

[AEM-gemeenschappen](/help/communities/overview.md) vereenvoudigen de oprichting en het beheer van on-premise gemeenschappen.

Hier worden enkele beste praktijken voor de Gemeenschappen beschreven:

|  |  |  |
|---|---|---|
| Aanbevolen werkwijzen voor het werken met door de gebruiker gegenereerde inhoud (UGC) | [Codeerrichtlijnen](/help/communities/code-guide.md) | Richtsnoeren voor de ontwikkeling van flexibele, draagbare code voor het [sociale kader](/help/communities/scf.md) (SCF). |
| Voorbeeld van het gebruik van communautaire componenten | [Community Components Guide](/help/communities/components-guide.md) | Een interactief ontwikkelingsprogramma. |

## Tooling/HTL {#tooling-htl}

HTML Template Language (HTL) is een nieuw HTML-sjabloonsysteem dat is geïntroduceerd met AEM 6.0. JSP en ESP worden vervangen als voorkeurssjabloonsysteem van AEM.

|  |  |  |
|---|---|---|
| HTML-overzicht | [HTML-overzicht en -syntaxis](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) | In dit document wordt beschreven wat HTML is, hoe u naar HTML kunt gaan, een voorbeeldproject, syntaxis, expressies en instructies |
| API gebruiken in Java | [HTML Java Use-API](https://helpx.adobe.com/experience-manager/htl/using/use-api.html) | Met de HTML Java Use-API kan een HTML-bestand toegang krijgen tot hulplijnmethoden in een aangepaste Java-klasse. |

>[!NOTE]
>
>De volgende meerdelige zelfstudie zou van belang kunnen zijn voor de beste praktijken om een nieuw AEM-project op te zetten, die de Componenten van de Kern, Bewerkbare Malplaatjes, de Bibliotheken van de Cliënt en de componentenontwikkeling detailleert:
>[Getting Started with AEM Sites - WKND Tutorial](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html)

