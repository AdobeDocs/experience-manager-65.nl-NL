---
title: Essentiële elementen van catalogus
seo-title: Essentiële elementen van catalogus
description: Overzicht van catalogus
seo-description: Overzicht van catalogus
uuid: 788512bb-fa38-48fb-a769-1eaae6bb95a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 542467ef-3793-4347-8424-c365c5a166f6
translation-type: tm+mt
source-git-commit: 41de9fff615b5b2f77d835740dfb1d33aa81e59b
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 3%

---


# Essentiële elementen van catalogus {#catalog-essentials}

Deze pagina bevat de essentiële informatie voor het werken met de catalogusfunctie van websites van gemeenschappen die deze functie inschakelen.

Met de catalogusfunctie kunnen leden van de gemeenschap bladeren naar en instellingsbronnen selecteren die in een catalogus staan.

Met de [ `enablement catalog` component](catalog.md) hebben leden van de gemeenschap toegang tot een catalogus met [enablement resources](resources.md). Het gebruik van AEM-tags is een belangrijk onderdeel van het beheer van de weergave van activeringsbronnen in een catalogus.

Zie [Tags toewijzen Bronnen](tag-resources.md).

## Essentiële elementen voor client-side {#essentials-for-client-side}

<table>
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td>
   <td>social/enablement/components/hbs/catalog</td>
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclusief</strong></a></td>
   <td>Nee</td>
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td>
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.catalog<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td>
  </tr>
  <tr>
   <td> <strong>templates</strong></td>
   <td> /libs/social/enablement/components/hbs/catalog/catalog.hbs<br /> </td>
  </tr>
  <tr>
   <td> <strong>css</strong></td>
   <td> /libs/social/enablement/components/hbs/catalog/clientlibs/catalog.css</td>
  </tr>
  <tr>
   <td><strong> eigenschappen</strong></td>
   <td>Zie <a href="catalog.md">Catalogusfunctie</a></td>
  </tr>
 </tbody>
</table>

## Essentiële elementen voor server-side {#essentials-for-server-side}

### Catalogusfunctie {#catalog-function}

Een community-sitestructuur die de [Catalogusfunctie](functions.md#catalog-function) bevat, bevat een geconfigureerde `enablement catalog`-component.

### Voorfilters {#pre-filters}

Wanneer een functie van de Catalogus aan een communautaire plaats is toegevoegd, is het mogelijk om de enablement middelen en de leerwegen te beperken die in de catalogus door een pre-filter te specificeren verschijnen. Dit wordt gedaan door eigenschappen op de instantie van het catalogusmiddel voor de plaats te plaatsen.

Het voorbeeld van [Enablement Tutorial](getting-started-enablement.md) gebruiken:

* Op auteur
* [CRXDE](../../help/sites-developing/developing-with-crxde-lite.md) gebruiken

   * Bijvoorbeeld [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)

* Ga naar de catalogusbron op de cataloguspagina

   * Bijvoorbeeld, `/content/sites/enable/en/catalog/jcr:content/content/primary/catalog`

* Een onderliggende filternode toevoegen

   * Selecteer de `catalog`node
   * Selecteer **[!UICONTROL Create Node]**

      * Naam: `filters`
      * Type: `nt:unstructured`
      * Selecteer **[!UICONTROL Save All]**

* `se_resource-tags`-eigenschap toevoegen aan het `filters`-knooppunt

   * Selecteer de `filters` knoop
   * Een eigenschap voor meerdere objecten toevoegen

      * Naam: `se_resource-tags`
      * Type: String
      * Waarde: *&lt;enter a [TagID](#pre-filter-tagids)*
         * Selecteer **[!UICONTROL Multi]**
         * Selecteer **[!UICONTROL Add]**

            * Selecteer `+` in het pop-updialoogvenster om extra voorfilter-id&#39;s toe te voegen

* De communitysite opnieuw publiceren

![configure-catalog](assets/configure-catalog.png)

#### Label-id&#39;s {#pre-filter-tagids} vóór filter

Het voorfilter [TagIDs](../../help/sites-developing/framework.md#tagid) moet exact overeenkomen met de tags die zijn toegepast op de instellingsbronnen. Deze worden in de map `resources` voor de site weergegeven als de waarden van de eigenschap `se_resource-tags`.

![configure-filters](assets/configure-catalog1.png)

### Referentie-API&#39;s {#reference-apis}

* [Inschakelings-API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/client/api/package-summary.html)

* [API voor rapportage](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/client/reporting/api/package-summary.html)

* [API voor analyse van rapporten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/client/reporting/analytics/api/package-summary.html)

