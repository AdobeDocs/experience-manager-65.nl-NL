---
title: Best practices implementeren
description: Leer hoe u Adobe Experience Manager (AEM) op de meest efficiënte en effectieve manier kunt implementeren en onderhouden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 4cbc0a30-d5f6-40ff-b7f6-8d64762e1970
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Best practices implementeren{#deploying-best-practices}

Met behulp van best practices wordt beschreven hoe Adobe Experience Manager (AEM) op de meest efficiënte en effectieve manier kan worden geïmplementeerd of onderhouden. Deze groeiende lijst met onderwerpen omvat verschillende gebieden in AEM.

Op de volgende gebieden is documentatie beschikbaar over het implementeren en onderhouden van best practices en aanbevelingen:

* [Eik](#oak)
* [Gemeenschappen](#communities)
* [UI](#ui)
* [Prestaties](#performance)

Raadpleeg een van de volgende bronnen voor beste praktijken bij het beheren, ontwikkelen of ontwerpen:

* [Aanbevolen werkwijzen beheren](/help/sites-administering/administer-best-practices.md)
* [Aanbevolen werkwijzen ontwikkelen](/help/sites-developing/best-practices.md)
* [Aanbevolen werkwijzen ontwerpen](/help/sites-authoring/best-practices.md)

In de volgende tabellen worden specifieke documenten beschreven en aan deze documenten gekoppeld.

## Eik {#oak}

[Eik](/help/sites-deploying/platform.md) is een schaalbare en krachtige hiërarchische opslagplaats voor inhoud die de basis vormt van AEM.

<table>
 <tbody>
  <tr>
   <td><p>Schaalbaarheid, prestaties en noodherstel</p> </td>
   <td><a href="/help/sites-deploying/performance.md">Prestaties en schaalbaarheid</a></td>
   <td>Biedt een witboek waarin de technische flexibiliteit, hoge prestaties en functies voor noodherstel van geluid worden besproken</td>
  </tr>
  <tr>
   <td>Aanbevolen Oak-implementaties</td>
   <td><a href="/help/sites-deploying/recommended-deploys.md">Aanbevolen implementaties</a></td>
   <td>Beschrijft plaatsingsscenario's</td>
  </tr>
  <tr>
   <td>Mongotopologie</td>
   <td><a href="/help/sites-deploying/recommended-deploys.md">Tips en trucs voor mongotopologie</a></td>
   <td>Beschrijft mongotopologie - wanneer om welke topologie te gebruiken.</td>
  </tr>
  <tr>
   <td>Datastore-opties</td>
   <td><a href="/help/sites-deploying/data-store-config.md">Het vormen knoop en gegevensopslag</a></td>
   <td>In dit document worden de aanbevolen procedures voor het opslaan van binaire gegevens en inhoudsknooppunten uitgelegd. Bevat informatie over het gebruik van de Amazon S3-gegevensopslag.</td>
  </tr>
  <tr>
   <td>Zoeken in eiken</td>
   <td><a href="/help/sites-deploying/best-practices-for-queries-and-indexing.md">Beste praktijken voor Vragen en het Indexeren</a><br /> </td>
   <td>Beschrijft beste praktijken op hoe te om inhoud te indexeren.</td>
  </tr>
 </tbody>
</table>

## Gemeenschappen {#communities}

AEM Communities vereenvoudigt de oprichting en het beheer van on-premise gemeenschappen. De beste praktijken voor AEM Communities worden hier beschreven:

[Community Content Store](/help/communities/working-with-srp.md) - Bespreekt de nieuwe gedeelde opslageigenschap voor gebruiker-geproduceerde inhoud (UGC) en de overwegingen voor het kiezen van het onderliggende [topologie](/help/communities/topologies.md).

[Aanbevolen implementaties voor gemeenschappen](/help/sites-deploying/recommended-deploys.md#considerations-for-aem-communities) - Beschrijft de geadviseerde plaatsingen voor Gemeenschappen. |

## UI {#ui}

De beste werkwijzen rond de gebruikersinterface worden hier beschreven:

[Gebruikersinterface Recommendations voor klanten](/help/sites-deploying/ui-recommendations.md)

AEM heeft momenteel twee gebruikersinterface&#39;s: klassieke gebruikersinterface en interface met aanraakfunctionaliteit in dezelfde release. Daarom moeten klanten een besluit nemen over welk gebruik tijdens de uitvoering van het project moet worden gemaakt. Dit document is bedoeld om u te helpen bij het zoeken naar de juiste keuze.

## Prestaties {#performance}

Hier worden aanbevolen werkwijzen weergegeven met betrekking tot prestaties:

<table>
 <tbody>
  <tr>
   <td>Beste praktijken voor kwaliteitsborging</td>
   <td><a href="/help/sites-deploying/configuring-performance.md#best-practices-for-quality-assurance">Beste praktijken voor kwaliteitsborging</a></td>
   <td>Een gestandaardiseerd overzicht van de kwesties betrokken bij het bepalen van een Concept van de Test specifiek voor prestatietests op uw <em>publish</em> milieu. Dit is hoofdzakelijk van belang voor ingenieurs QA, projectmanagers, en systeembeheerders.</td>
  </tr>
  <tr>
   <td>Dispatcher gebruiken met een CDN</td>
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html#using-dispatcher-with-a-cdn">Dispatcher gebruiken met een CDN</a></td>
   <td>Een CDN (Content Delivery Network), zoals Akamai Edge Delivery of Amazon Cloud Front, levert inhoud op een locatie die dicht bij de eindgebruiker ligt.</td>
  </tr>
  <tr>
   <td>Optimalisatie van prestaties</td>
   <td><a href="/help/sites-deploying/configuring-performance.md">Optimalisatie van prestaties</a></td>
   <td>Een belangrijk probleem is de tijd die uw website nodig heeft om te reageren op bezoekersverzoeken.</td>
  </tr>
  <tr>
   <td>Prestatietesten</td>
   <td><a href="/help/sites-deploying/best-practices-for-performance-testing.md">Best practices voor het testen van prestaties</a></td>
   <td>Beschrijft beste praktijken voor het runnen van prestatietests op een AEM plaatsing.<br /> </td>
  </tr>
 </tbody>
</table>
