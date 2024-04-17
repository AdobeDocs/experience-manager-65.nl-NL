---
title: Beste praktijken voor AEM ontwikkelaars
description: De Techniek en de Raadgevende teams van de Adobe hebben een uitvoerige reeks beste praktijken voor AEM ontwikkelaars ontwikkeld.
contentOwner: Justin Edelson
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 0a478e80-c1b2-46c1-a6be-794d78b85d69
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# Aanbevolen procedures{#best-practices}

## Aanbevolen procedures voor ontwikkelaars - Aan de slag {#best-practices-for-developers-getting-started}

De Techniek en de Raadgevende teams van de Adobe hebben een uitvoerige reeks beste praktijken voor AEM ontwikkelaars ontwikkeld. De ontwikkelaar van de Adobe houdt zich aan deze beste praktijken aangezien zij kern AEM productupdates en klantencode voor klantenimplementaties ontwikkelen.

Voordat u uw AEM ontwikkelingsproject start, moet u eerst de volgende aanbevolen procedures doornemen:

* [Ontwikkelspraktijken](/help/sites-developing/development-practices.md)
* [Inhoud architectuur](/help/sites-developing/content-architecture.md)
* [Softwarearchitectuur](/help/sites-developing/software-architecture.md)
* [Codetips](/help/sites-developing/coding-tips.md)
* [Codepitten](/help/sites-developing/code-pitfalls.md)
* [JCR-interactie](/help/sites-developing/jcr-integration.md)
* [OSGi-bundels](/help/sites-developing/osgi-bundles.md)
* [Aanbevolen werkwijzen voor Java API](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

### Aanvullende informatie over aanbevolen procedures {#additional-best-practices-information}

Op de volgende gebieden is documentatie beschikbaar die specifiek is voor de ontwikkeling van beste praktijken:

* [Sites](#sites)
* [Gemeenschappen](/help/sites-developing/best-practices.md#communities)
* [Tooling/HTL](/help/sites-developing/best-practices.md#tooling-htl)

In de volgende tabellen worden specifieke documenten beschreven en aan deze documenten gekoppeld.

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
   <td><p><a href="/help/sites-developing/touch-ui-concepts.md">Interface met aanraakbediening: concepten</a></p> <p><a href="/help/sites-developing/touch-ui-structure.md">Interface voor touch-functies: structuur</a></p> </td>
   <td>Deze documenten bieden een overzicht van de concepten en structuur van de interface met aanraakbediening.</td>
  </tr>
  <tr>
   <td>Interface met aanraakbediening: consoles aanpassen </td>
   <td><a href="/help/sites-developing/customizing-consoles-touch.md">UI-consoles met aanraakbediening aanpassen</a></td>
   <td>In dit document wordt beschreven hoe u de consoles voor de interface met aanraakbediening het beste kunt uitbreiden.</td>
  </tr>
  <tr>
   <td>Interface met aanraakbediening: pagina's ontwerpen aanpassen</td>
   <td><a href="/help/sites-developing/customizing-page-authoring-touch.md">UI-pagina's met aanraakbediening aanpassen</a></td>
   <td>Beschrijft hoe te om paginaontwerp voor aanraking-toegelaten UI uit te breiden.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td><a href="/help/sites-developing/workflows-best-practices.md">Workflows ontwikkelen en uitbreiden</a></td>
   <td><p>Met workflows kunt u Adobe Experience Manager-activiteiten (AEM) automatiseren en een groot deel van de verwerking in een AEM omgeving vertegenwoordigen. Daarom wordt u ten zeerste aangeraden de implementatie van workflows zorgvuldig te plannen.</p> </td>
  </tr>
 </tbody>
</table>

## Gemeenschappen {#communities}

[AEM Communities](/help/communities/overview.md) vereenvoudigt de oprichting en het beheer van on-premise Gemeenschappen.

Hier worden enkele beste praktijken voor de Gemeenschappen beschreven:

|  |  |  |
|---|---|---|
| Aanbevolen werkwijzen voor het werken met door de gebruiker gegenereerde inhoud (UGC) | [Codeerrichtlijnen](/help/communities/code-guide.md) | Richtsnoeren voor de ontwikkeling van flexibele, draagbare code voor de [sociale component](/help/communities/scf.md) (SCF). |
| Voorbeeld van het gebruik van communautaire componenten | [Community Components Guide](/help/communities/components-guide.md) | Een interactief ontwikkelingsprogramma. |

## Tooling/HTL {#tooling-htl}

HTML Sjabloontaal (HTL) is een nieuw sjabloonsysteem voor HTML, dat is geïntroduceerd met AEM 6.0. JSP en ESP worden vervangen als het voorkeurssjabloonsysteem voor AEM.

|  |  |  |
|---|---|---|
| HTML-overzicht | [HTML-overzicht en -syntaxis](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html) | In dit document wordt beschreven wat HTML is, hoe u naar HTML kunt gaan, een voorbeeldproject, syntaxis, expressies en instructies |
| API gebruiken in Java | [HTML Java Use-API](https://helpx.adobe.com/experience-manager/htl/using/use-api.html) | De HTML Java Use-API stelt een HTML-bestand in staat toegang te krijgen tot hulplijnmethoden in een aangepaste Java-klasse. |

>[!NOTE]
>
>De volgende meerdelige zelfstudie kan van belang zijn voor de beste praktijken om een nieuw AEM project op te zetten, die de Componenten van de Kern, Bewerkbare Malplaatjes, de Bibliotheken van de Cliënt en de componentenontwikkeling detailleert:
>[Aan de slag met AEM Sites - WKND-zelfstudie](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html)
