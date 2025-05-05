---
title: Dashboards
description: Leer hoe u nieuwe AEM-dashboards maakt, configureert en ontwikkelt.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: 5b934e3a-f554-46ec-a913-8d570abb1503
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 0%

---

# Dashboards{#dashboards}

Wanneer u AEM gebruikt, kunt u een groot aantal verschillende typen inhoud beheren (bijvoorbeeld pagina&#39;s, elementen). AEM dashboards verstrekken een makkelijk te gebruiken en aanpasbare manier om pagina&#39;s te bepalen die geconsolideerde gegevens tonen.

>[!NOTE]
>
>AEM dashboards worden gecreeerd op een per gebruikersbasis, zodat kan een gebruiker tot hun eigen dashboard slechts toegang hebben.
>
>Nochtans, {de malplaatjes van 0} Dashboard [&#128279;](#creating-a-dashboard-template) kunnen worden gebruikt om gemeenschappelijke configuratie en lay-out te delen Dashboard.

![ chlimage_1-22 ](assets/chlimage_1-22.jpeg)

## Dashboards beheren {#administering-dashboards}

### Een dashboard maken {#creating-a-dashboard}

1. In de **sectie van Hulpmiddelen**, klik **Console van de Configuratie**.
1. In de boom, klik **Dashboard** tweemaal.
1. Klik **Nieuw Dashboard**.
1. Typ de **Titel** (bijvoorbeeld, Mijn Dashboard) en de **Naam**.
1. Klik **creëren**.

### Een dashboard klonen {#cloning-a-dashboard}

Mogelijk wilt u meerdere dashboards hebben om snel informatie over uw inhoud vanuit verschillende weergaven te bekijken. AEM biedt een kloonfunctie waarmee u een bestaand dashboard kunt dupliceren, zodat u een nieuw dashboard kunt maken. Ga als volgt te werk om een dashboard te klonen:

1. In de **sectie van Hulpmiddelen**, klik **Console van de Configuratie**.

1. In de boom, klik **Dashboard**.
1. Klik op het dashboard dat u wilt klonen.

1. Klik **Kloon**.

1. Typ de **Naam** van uw nieuw dashboard.

### Een dashboard verwijderen {#removing-a-dashboard}

1. In de **sectie van Hulpmiddelen**, klik **Console van de Configuratie**.

1. In de boom, klik **Dashboard**.
1. Klik op het dashboard dat u wilt verwijderen.

1. Klik **verwijderen**.

1. Klik **ja** om te bevestigen.

## Dashboardcomponenten {#dashboard-components}

### Overzicht {#overview}

De componenten van het dashboard zijn niets meer dan regelmatige [ AEM componenten ](/help/sites-developing/developing-components-samples.md). In deze sectie worden de rapportonderdelen beschreven die bij AEM worden geleverd.

### Webanalytische rapportagecomponenten {#web-analytics-reporting-components}

AEM schepen met een reeks componenten die veelvoudige metriek van uw [ SiteCatalyst ](/help/sites-administering/adobeanalytics.md) gegevens teruggeven. Die componenten zijn vermeld in de Sidekick onder de **sectie van het dashboard**.

Elke rapportcomponent bevat ten minste drie tabbladen:

* **Basis**: bevat de belangrijkste configuratie.

* **Rapport:** bevat de configuratie specifiek van elk rapport.
* **Stijl**: bevat het stileren configuratie zoals grafiekgrootte en marge.

De rapportcomponenten worden geïnitialiseerd met een standaardconfiguratie die u helpt snel opstelling uw dashboard.

#### Basisconfiguratie {#basic-configuration}

Het **Basis** lusje verleent toegang tot de volgende configuratieingangen:

**Titel** de titel die op het dashboard wordt getoond.

**het type van Verzoek** De manier de gegevens worden gevraagd.

**de Configuratie van de SiteCatalyst (facultatief)** de configuratie u wilt gebruiken om met SiteCatalyst te verbinden. Indien niet verstrekt wordt de configuratie verondersteld om op de pagina van het Dashboard (via paginaeigenschappen) te worden gevormd.

**identiteitskaart van de Reeks van het Rapport (facultatief)** de het rapportreeks van de SiteCatalyst u wilt gebruiken om de grafiek te produceren.

#### Rapportconfiguratie {#report-configuration}

Als u webstatistieken wilt weergeven, moet u het datumbereik definiëren van de gegevens die u wilt genereren. Het **lusje van het Rapport** verstrekt twee gebieden om die waaier te bepalen.

>[!NOTE]
>
>Als u een datumbereik voor een grote datum instelt, kan de reactiesnelheid van het dashboard afnemen.

**Datum van** Absolute of relatieve datum waarvan het gegeven wordt gehaald.

**Datum aan** Absolute of relatieve datum waaraan het gegeven wordt gehaald.

Elke component definieert ook specifieke instellingen.

#### Rapport overuren {#overtime-report}

![ chlimage_1-26 ](assets/chlimage_1-26a.png)

**Eenheid van de Tijd van de Korreligheid van de Datum van 0&rbrace; &lbrace;(bijvoorbeeld, dag, uur).**

**Metriek** de lijst van gebeurtenissen u wilt tonen.

**Elementen** de lijst van elementen die de metrieke gegevens in de grafiek opsplitsen.

#### Rapport met gerangschikte lijst {#ranked-list-report}

![ chlimage_1-27 ](assets/chlimage_1-27a.png)

**Elementen** het element dat de metrieke gegevens in de grafiek opsplitst.

**Metriek** de gebeurtenis u wilt tonen.

**Nr. van hoogste punten** Aantal punten die door het rapport worden getoond.

#### Geregistreerd rapport {#ranked-report}

![ chlimage_1-28 ](assets/chlimage_1-28a.png)

**Metriek** de gebeurtenis u wilt tonen.

**Elementen** het element dat de metrieke gegevens in de grafiek opsplitst.

#### Rapport voor bovenste site-sectie {#top-site-section-report}

Deze component geeft een grafiek weer met de meer bezochte sectie van een website volgens de volgende configuratie.

![ chlimage_1-29 ](assets/chlimage_1-29a.png)

**Nr. van hoogste punten** Aantal sectie die door in het rapport wordt getoond.

#### Trend Report {#trended-report}

![ chlimage_1-30 ](assets/chlimage_1-30a.png)

**Eenheid van de Tijd van de Korreligheid van de Datum van 0&rbrace; &lbrace;(bijvoorbeeld, dag, uur).**

**Metriek** de gebeurtenis u wilt tonen.

**Elementen** het element dat de metrieke gegevens in de grafiek opsplitst.

## Het dashboard uitbreiden {#extending-dashboard}

### Overzicht {#overview-1}

Dashboards zijn normale pagina&#39;s ( `cq:Page`), daarom kunnen om het even welke componenten worden gebruikt om Dashboards samen te stellen.

Er is een standaardcomponentengroep `Dashboard` die analytische rapportcomponenten bevat die standaard op de sjabloon zijn ingeschakeld.

### Een dashboardsjabloon maken {#creating-a-dashboard-template}

Een sjabloon definieert de standaardinhoud van een nieuw dashboard. U kunt verschillende sjablonen gebruiken voor het maken van verschillende typen dashboards.

Dashboardsjablonen worden net als andere paginasjablonen gemaakt, maar worden opgeslagen onder `/libs/cq/dashboards/templates/` . Zie [ Creërend het Malplaatje van de Inhoud ](/help/sites-developing/website.md#creating-the-contentpage-template) sectie.

>[!NOTE]
>
>Dashboardsjablonen worden door gebruikers gedeeld.

### Een dashboardcomponent ontwikkelen {#developing-a-dashboard-component}

Het ontwikkelen van een dashboardcomponent bestaat uit het maken van een gewone AEM. Deze sectie beschrijft een voorbeeld van een component die hoogste 10 van contribuanten toont.

![ chlimage_1-31 ](assets/chlimage_1-31a.png)

De bovenste auteurcomponenten worden opgeslagen in de bewaarplaats bij `/apps/geometrixx-outdoors/components/reporting` en bestaan uit:

1. een `jsp` -bestand waarin jcr-gegevens worden gelezen en de tijdelijke aanduiding `html` wordt gedefinieerd.

1. een client-side bibliotheek met één `js` -bestand dat de gegevens ophaalt en bestelt, vult vervolgens de tijdelijke aanduiding `html` .

![ chlimage_1-32 ](assets/chlimage_1-32a.png)

Het volgende dossier van JavaScript wordt bepaald in de `geout.reporting.topauthors` [ Bibliotheek van de Cliënt ](/help/sites-developing/clientlibs.md) als kind van de component zelf.

[ QueryBuilder ](/help/sites-developing/querybuilder-api.md) wordt gebruikt om de bewaarplaats te vragen om `cq:AuditEvent` knopen te lezen. Het queryresultaat is een JSON-object waaruit de bijdragen van de auteur worden geëxtraheerd.

#### top_authors.js {#top-authors-js}

```
$.ajax({
  url: "/bin/querybuilder.json",
  cache: false,
  data: {
       "orderby": "cq:time",
       "orderby.sort": "desc",
       "p.hits": "full",
       "p.limit": 100,
       "path": "/var/audit/com.day.cq.wcm.core.page/",
       "type": "cq:AuditEvent"
   },
  dataType: "json"
}).done(function( res ) {
    var authors = {};
    // from JSON to Object
    for(var r in res.hits) {
        var userId = res.hits[r].userId;
        if(userId == undefined) {
            continue;
        }
        var auth = authors[userId] || {userId : userId};
        auth.contrib = (auth.contrib || 0) +1;

        authors[userId] = auth;
    }

    // order by contribution
    var orderedByContrib = [];
    for(var a in authors) {
        orderedByContrib.push(authors[a]);
    }
    orderedByContrib.sort(function(a,b){return b.contrib - a.contrib});

    // produce the list
    for (var i=0, tot=orderedByContrib.length; i < tot; i++) {
        var current = orderedByContrib[i];
        $("<div> #" + (i + 1) +" "+ current.userId + " (" + current.contrib +" contrib.)</div>").appendTo("#authors-list");

    }
});
```

`JSP` bevat zowel `global.jsp` als `clientlib` .

#### top_authors.jsp {#top-authors-jsp}

```java
<%@page session="false" contentType="text/html; charset=utf-8" %><%
%><%
%><%@include file="/libs/foundation/global.jsp" %><%
%>
<ui:includeClientLib categories="geout.reporting.topauthors" />
<%
String reportletTitle = properties.get("title", "Top Authors");
%>
<html>
     <h3><%=xssAPI.encodeForHTML(reportletTitle) %></h3>
     <div id="authors-list"></div>
</html>
```
