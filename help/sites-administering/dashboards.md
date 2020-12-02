---
title: Dashboards
seo-title: Dashboards
description: Leer hoe u nieuwe AEM-dashboards maakt, configureert en ontwikkelt.
seo-description: Leer hoe u nieuwe AEM-dashboards maakt, configureert en ontwikkelt.
uuid: 3eadbba2-0ce1-41be-a9f8-e6cafa109893
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 40560e06-2508-45a4-a648-39629ed54f28
translation-type: tm+mt
source-git-commit: 69dfd6b41b32cb9131fd90fd7039a0c224889db5
workflow-type: tm+mt
source-wordcount: '846'
ht-degree: 0%

---


# Dashboards{#dashboards}

Wanneer u AEM gebruikt, kunt u veel verschillende inhoudstypen beheren (zoals pagina&#39;s, elementen). AEM dashboards verstrekken een makkelijk te gebruiken en aanpasbare manier om pagina&#39;s te bepalen die geconsolideerde gegevens tonen.

>[!NOTE]
>
>AEM dashboards worden gecreeerd op een per gebruikersbasis, zodat kan een gebruiker tot hun eigen dashboard slechts toegang hebben.
>
>Nochtans, [kunnen de malplaatjes van het dashboard](#creating-a-dashboard-template) worden gebruikt om gemeenschappelijke configuratie en lay-out van het dashboard te delen.

![chlimage_1-22](assets/chlimage_1-22.jpeg)

## Dashboards beheren {#administering-dashboards}

### Een dashboard maken {#creating-a-dashboard}

Ga als volgt te werk om een nieuw dashboard te maken:

1. Klik in de sectie **Tools** op **Configuratieconsole**.
1. Dubbelklik in de structuur op **Dashboard**.
1. Klik **Nieuw dashboard**.
1. Typ de **Titel** (bijvoorbeeld Mijn dashboard) en **Naam**.
1. Klik **Maken**.

### Een dashboard klonen {#cloning-a-dashboard}

Mogelijk wilt u meerdere dashboards hebben om snel informatie over uw inhoud vanuit verschillende weergaven te bekijken. AEM biedt een kloonfunctie waarmee u een bestaand dashboard kunt dupliceren, zodat u een nieuw dashboard kunt maken. Ga als volgt te werk om een dashboard te klonen:

1. Klik in de sectie **Tools** op **Configuratieconsole**.

1. Klik in de structuur op **Dashboard**.
1. Klik op het dashboard dat u wilt klonen.

1. Klik **Klonen**.

1. Typ de **Naam** van het nieuwe dashboard.

### Een dashboard verwijderen {#removing-a-dashboard}

1. Klik in de sectie **Tools** op **Configuratieconsole**.

1. Klik in de structuur op **Dashboard**.
1. Klik op het dashboard dat u wilt verwijderen.

1. Klik **Verwijderen**.

1. Klik **Ja** om te bevestigen.

## Dashboard-componenten {#dashboard-components}

### Overzicht {#overview}

De componenten van het dashboard zijn niets meer dan gewone [AEM componenten](/help/sites-developing/developing-components-samples.md). In deze sectie worden de rapportonderdelen beschreven die bij AEM worden geleverd.

### Webanalytische rapportagecomponenten {#web-analytics-reporting-components}

AEM wordt geleverd met een set componenten die meerdere metrische gegevens van uw [SiteCatalyst](/help/sites-administering/adobeanalytics.md)-gegevens renderen. Deze componenten worden vermeld in de Sidetrap onder de sectie **Dashboard**.

Elke rapportcomponent bevat ten minste drie tabbladen:

* **Standaard**: bevat de hoofdconfiguratie.

* **Rapport:** bevat de configuratie specifiek van elk rapport.
* **Stijl**: bevat opmaakconfiguratie zoals diagramgrootte en -marge.

De rapportcomponenten worden geïnitialiseerd met een standaardconfiguratie die u helpt snel opstelling uw dashboard.

#### Basisconfiguratie {#basic-configuration}

Het **Basis** lusje verleent toegang tot de volgende configuratieingangen:

**** TitleThe title displayed op the dashboard.

**Request-** typeDe manier waarop gegevens worden aangevraagd.

**SiteCatalyst Configuration (optioneel)** The configuration you want to use to connect to SiteCatalyst. Indien niet verstrekt wordt de configuratie verondersteld om op de pagina van het Dashboard (via paginaeigenschappen) te worden gevormd.

**ID rapportsuite (optioneel)** De SiteCatalyst-rapportsuite die u wilt gebruiken om de grafiek te genereren.

#### Rapportconfiguratie {#report-configuration}

Als u webstatistieken wilt weergeven, moet u het datumbereik definiëren van de gegevens die u wilt genereren. Het **tabblad Report** biedt twee velden om dat bereik te definiëren.

>[!NOTE]
>
>Als u een datumbereik voor een grote datum instelt, kan de reactiesnelheid van het dashboard afnemen.

**Datum** van Absolute of relatieve datum vanaf wanneer de gegevens worden opgehaald.

**Datum** tot absolute of relatieve datum waarop de gegevens zijn opgehaald.

Elke component definieert ook specifieke instellingen.

#### Rapport overuren {#overtime-report}

![chlimage_1-26](assets/chlimage_1-26a.png)

**Date** GranularityTime-eenheid van de X-as (bijvoorbeeld dag, uur).

**** MetricsThe list of events you want to display.

**** ElementsThe list of elements that break down the metrics data in the graph.

#### Rapport met gerangschikte lijst {#ranked-list-report}

![chlimage_1-27](assets/chlimage_1-27a.png)

**** ElementsHet element dat de meetgegevens in de grafiek opsplitst.

**** MetricsDe gebeurtenis die u wilt weergeven.

**Nee. van hoogste punten** Aantal punten die door het rapport worden getoond.

#### Geregistreerd rapport {#ranked-report}

![chlimage_1-28](assets/chlimage_1-28a.png)

**** MetricsDe gebeurtenis die u wilt weergeven.

**** ElementsHet element dat de meetgegevens in de grafiek opsplitst.

#### Rapport {#top-site-section-report} voor bovenste sectie

Deze component geeft een grafiek weer met de meer bezochte sectie van een website volgens de volgende configuratie.

![chlimage_1-29](assets/chlimage_1-29a.png)

**Nee. van hoogste punten** Aantal sectie die door in het rapport wordt getoond.

#### Trend rapport {#trended-report}

![chlimage_1-30](assets/chlimage_1-30a.png)

**Date** GranularityTime-eenheid van de X-as (bijvoorbeeld dag, uur).

**** MetricsDe gebeurtenis die u wilt weergeven.

**** ElementsHet element dat de meetgegevens in de grafiek opsplitst.

## Het dashboard {#extending-dashboard} uitbreiden

### Overzicht {#overview-1}

Dashboards zijn normale pagina&#39;s ( `cq:Page`), daarom kunnen om het even welke componenten worden gebruikt om Dashboards samen te stellen.

Er is een standaardcomponentengroep `Dashboard` die analytische rapportcomponenten bevat die door gebrek op het malplaatje worden toegelaten.

### Een dashboardsjabloon maken {#creating-a-dashboard-template}

Een sjabloon definieert de standaardinhoud van een nieuw dashboard. U kunt verschillende sjablonen gebruiken voor het maken van verschillende typen dashboards.

Dashboardsjablonen worden net als andere paginasjablonen gemaakt, maar worden opgeslagen onder `/libs/cq/dashboards/templates/`. Zie de sectie [Sjabloon voor inhoudspagina maken](/help/sites-developing/website.md#creating-the-contentpage-template).

>[!NOTE]
>
>Dashboardsjablonen worden door gebruikers gedeeld.

### Een dashboardcomponent {#developing-a-dashboard-component} ontwikkelen

Het ontwikkelen van een dashboardcomponent bestaat uit het maken van een gewone AEM. Deze sectie beschrijft een voorbeeld van een component die hoogste 10 van contribuanten toont.

![chlimage_1-31](assets/chlimage_1-31a.png)

De bovenste auteurcomponenten worden opgeslagen in de bewaarplaats op `/apps/geometrixx-outdoors/components/reporting` en bestaat uit:

1. een `jsp`-bestand dat jcr-gegevens leest en de tijdelijke aanduiding `html` definieert.

1. een client-side bibliotheek met één `js`-bestand dat de gegevens ophaalt en bestelt, vult vervolgens de tijdelijke aanduiding `html`.

![chlimage_1-32](assets/chlimage_1-32a.png)

Het volgende Javascript-bestand wordt in `geout.reporting.topauthors` [Clientbibliotheek](/help/sites-developing/clientlibs.md) gedefinieerd als een onderliggend item van de component zelf.

De [QueryBuilder](/help/sites-developing/querybuilder-api.md) wordt gebruikt om de opslagplaats te vragen om `cq:AuditEvent` knopen te lezen. Het queryresultaat is een JSON-object waaruit de bijdragen van de auteur worden geëxtraheerd.

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

`JSP` omvat zowel `global.jsp` als `clientlib`.

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

