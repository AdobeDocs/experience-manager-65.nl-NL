---
title: Essentiële toewijzingen
seo-title: Essentiële toewijzingen
description: Overzicht van de toewijzingsfuncties voor gemeenschappen die in staat zijn om te werken
seo-description: Overzicht van de toewijzingsfuncties voor gemeenschappen die in staat zijn om te werken
uuid: e49fce26-1091-4f37-93e8-c4ec85371811
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 6bac681e-59e1-4786-9c50-6679c936cfd1
docset: aem65
translation-type: tm+mt
source-git-commit: c897f034edbdbeee74869165ed384c3408a857e0
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Essentiële toewijzingen {#assignments-essentials}

Lees verder om over de essentiële informatie voor het werken met de taakeigenschap van [het toelaten van communautaire](/help/communities/overview.md#enablement-community) plaatsen te weten te komen.

De toewijzingsfunctie is de mogelijkheid om bronnen voor activering en leerpaden toe te wijzen aan leden van gemeenschappen die activering mogelijk maken.

## Essentiële elementen voor client-kant {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/enablement/components/hbs/myassigned</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="/help/communities/clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie <a href="/help/communities/assignments.md">Toewijzingsfunctie</a></td>
  </tr>
 </tbody>
</table>

### Voltooiings- en successtatus {#completion-and-success-status}

De voltooiings- en successtatus worden gebruikt in rapporten en statusbanners bij toewijzingen.

Voltooiingsstatus:

* Niet toegewezen
* Niet gestart (nieuw)
* In uitvoering
* Voltooid

Successtatus:

* Onbekend
* Voldoende
* Mislukt

De enige mogelijke combinaties van Voltooiing en Successtatus zijn:

| **Voltooiing** | **Succes** |
|---|---|
| Niet gestart | Onbekend |
| In uitvoering | Onbekend |
| Voltooid | Voldoende |
| Voltooid | Mislukt |

## Essentiële elementen voor server-side {#essentials-for-server-side}

### Toewijzingsfunctie {#assignments-function}

Een gemeenschapssitestructuur die de functie [](/help/communities/functions.md#assignments-function)Toewijzingen bevat, bevat een geconfigureerde ` [assignments](/help/communities/assignments.md)` component.

### Referentie-API&#39;s {#reference-apis}

* [Inschakelings-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API voor rapportage](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [Analytics API rapporteren](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)

