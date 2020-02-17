---
title: Dashboards
seo-title: Dashboards
description: Leer nieuwe AEM-dashboards maken, configureren en ontwikkelen.
seo-description: Leer nieuwe AEM-dashboards maken, configureren en ontwikkelen.
uuid: 3eadbba2-0ce1-41be-a9f8-e6cafa109893
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 40560e06-2508-45a4-a648-39629ed54f28
translation-type: tm+mt
source-git-commit: 69dfd6b41b32cb9131fd90fd7039a0c224889db5

---


# Dashboards{#dashboards}

Wanneer u AEM gebruikt, kunt u veel inhoud van verschillende typen beheren (bijvoorbeeld pagina&#39;s, elementen). AEM-dashboards bieden een gebruiksvriendelijke en aanpasbare manier om pagina&#39;s te definiëren waarop geconsolideerde gegevens worden weergegeven.

>[!NOTE]
>
>AEM-dashboards worden gemaakt per gebruiker, zodat een gebruiker alleen toegang heeft tot zijn of haar eigen dashboard.
>
>Nochtans, kunnen de malplaatjes [van het](#creating-a-dashboard-template) dashboard worden gebruikt om gemeenschappelijke configuratie en lay-out te delen Dashboard.

![chlimage_1-22](assets/chlimage_1-22.jpeg)

## Dashboards beheren {#administering-dashboards}

### Een dashboard maken {#creating-a-dashboard}

Ga als volgt te werk om een nieuw dashboard te maken:

1. Klik in de sectie **Gereedschappen** op **Configuratieconsole**.
1. Dubbelklik in de structuur op **dashboard**.
1. Klik op **Nieuw dashboard**.
1. Typ de **titel** (bijvoorbeeld Mijn dashboard) en de **naam**.
1. Klik op **Maken**.

### Een dashboard klonen {#cloning-a-dashboard}

Mogelijk wilt u meerdere dashboards hebben om snel informatie over uw inhoud vanuit verschillende weergaven te bekijken. Om u te helpen om een nieuw dashboard te maken, biedt AEM een kloonfunctie waarmee u een bestaand dashboard kunt dupliceren. Ga als volgt te werk om een dashboard te klonen:

1. Klik in de sectie **Gereedschappen** op **Configuratieconsole**.

1. Klik in de structuur op **Dashboard**.
1. Klik op het dashboard dat u wilt klonen.

1. Klik op **Klonen**.

1. Typ de **naam** van het nieuwe dashboard.

### Een dashboard verwijderen {#removing-a-dashboard}

1. Klik in de sectie **Gereedschappen** op **Configuratieconsole**.

1. Klik in de structuur op **Dashboard**.
1. Klik op het dashboard dat u wilt verwijderen.

1. Klik op **Verwijderen**.

1. Klik op **Ja** om te bevestigen.

## Dashboardcomponenten {#dashboard-components}

### Overzicht {#overview}

Dashboardcomponenten zijn niets meer dan gewone [AEM-componenten](/help/sites-developing/developing-components-samples.md). In deze sectie worden de rapportonderdelen beschreven die bij AEM worden geleverd.

### Webanalytische rapportagecomponenten {#web-analytics-reporting-components}

AEM wordt geleverd met een set componenten die meerdere metriek van uw [SiteCatalyst](/help/sites-administering/adobeanalytics.md) -gegevens renderen. Deze componenten worden vermeld in de Sidetrap onder de sectie **Dashboard** .

Elke rapportcomponent bevat ten minste drie tabbladen:

* **Standaard**: bevat de hoofdconfiguratie.

* **** Rapport: bevat specifiek de configuratie van elk rapport.
* **Stijl**: bevat opmaakconfiguratie zoals diagramgrootte en -marge.

De rapportcomponenten worden geïnitialiseerd met een standaardconfiguratie die u helpt snel opstelling uw dashboard.

#### Basisconfiguratie {#basic-configuration}

Het tabblad **Standaard** biedt toegang tot de volgende configuratiegegevens:

**Titel** De titel die op het dashboard wordt weergegeven.

**Type** verzoek De manier waarop gegevens worden aangevraagd.

**SiteCatalyst-configuratie (optioneel)** De configuratie die u wilt gebruiken om verbinding te maken met SiteCatalyst. Indien niet verstrekt wordt de configuratie verondersteld om op de pagina van het Dashboard (via paginaeigenschappen) te worden gevormd.

**ID rapportsuite (optioneel)** De SiteCatalyst-rapportsuite die u wilt gebruiken om de grafiek te genereren.

#### Rapportconfiguratie {#report-configuration}

Als u webstatistieken wilt weergeven, moet u het datumbereik definiëren van de gegevens die u wilt genereren. Het tabblad **Rapport** bevat twee velden waarmee dat bereik wordt gedefinieerd.

>[!NOTE]
>
>Als u een datumbereik voor een grote datum instelt, kan de reactiesnelheid van het dashboard afnemen.

**Datum vanaf** Absolute of relatieve datum vanaf wanneer de gegevens worden opgehaald.

**Datum tot** absolute of relatieve datum waarop de gegevens worden opgehaald.

Elke component definieert ook specifieke instellingen.

#### Rapport overuren {#overtime-report}

![chlimage_1-26](assets/chlimage_1-26a.png)

**Datum granularity** Time eenheid van de as van X (b.v. dag, uur).

**Metrisch** De lijst met gebeurtenissen die u wilt weergeven.

**Elementen** De lijst met elementen waarmee de metagegevens in de grafiek worden gesplitst.

#### Rapport met gerangschikte lijst {#ranked-list-report}

![chlimage_1-27](assets/chlimage_1-27a.png)

**Elementen** Het element dat de cijfergegevens in de grafiek opsplitst.

**Metrisch** De gebeurtenis die u wilt weergeven.

**Nee. van bovenste items** Aantal items dat door het rapport wordt weergegeven.

#### Geregistreerd rapport {#ranked-report}

![chlimage_1-28](assets/chlimage_1-28a.png)

**Metrisch** De gebeurtenis die u wilt weergeven.

**Elementen** Het element dat de cijfergegevens in de grafiek opsplitst.

#### Rapport voor bovenste sectie {#top-site-section-report}

Deze component geeft een grafiek weer met de meer bezochte sectie van een website volgens de volgende configuratie.

![chlimage_1-29](assets/chlimage_1-29a.png)

**Nee. van hoogste punten** Aantal sectie die door in het rapport wordt getoond.

#### Trend Report {#trended-report}

![chlimage_1-30](assets/chlimage_1-30a.png)

**Datum granularity** Time eenheid van de as van X (b.v. dag, uur).

**Metrisch** De gebeurtenis die u wilt weergeven.

**Elementen** Het element dat de cijfergegevens in de grafiek opsplitst.

## Het dashboard uitbreiden {#extending-dashboard}

### Overzicht {#overview-1}

Dashboards zijn normale pagina&#39;s ( `cq:Page`), daarom kunnen om het even welke componenten worden gebruikt om dashboards samen te stellen.

Er is een standaardcomponentengroep `Dashboard` die analytische rapporteringscomponenten bevat die op het malplaatje door gebrek worden toegelaten.

### Een dashboardsjabloon maken {#creating-a-dashboard-template}

Een sjabloon definieert de standaardinhoud van een nieuw dashboard. U kunt verschillende sjablonen gebruiken voor het maken van verschillende typen dashboards.

Dashboardsjablonen worden net als andere paginasjablonen gemaakt, maar worden onder opgeslagen `/libs/cq/dashboards/templates/`. Zie de sectie Sjabloon [voor inhoudspagina](/help/sites-developing/website.md#creating-the-contentpage-template) maken.

>[!NOTE]
>
>Dashboardsjablonen worden door gebruikers gedeeld.

### Een dashboardcomponent ontwikkelen {#developing-a-dashboard-component}

Het ontwikkelen van een dashboardcomponent bestaat uit het maken van een gewone AEM-component. Deze sectie beschrijft een voorbeeld van een component die hoogste 10 van contribuanten toont.

![chlimage_1-31](assets/chlimage_1-31a.png)

De bovenste auteurcomponenten worden opgeslagen in de bewaarplaats bij `/apps/geometrixx-outdoors/components/reporting` en zijn samengesteld uit:

1. een `jsp` bestand waarin jcr-gegevens worden gelezen en de `html` tijdelijke aanduiding wordt gedefinieerd.

1. een bibliotheek aan de clientzijde met één `js` bestand dat de gegevens ophaalt en bestelt en vervolgens de `html` plaatsaanduiding invult.

![chlimage_1-32](assets/chlimage_1-32a.png)

Het volgende Javascript-bestand wordt in de `geout.reporting.topauthors` clientbibliotheek [](/help/sites-developing/clientlibs.md) gedefinieerd als een onderliggend item van de component zelf.

De [VraagBuilder](/help/sites-developing/querybuilder-api.md) wordt gebruikt om de bewaarplaats te vragen om `cq:AuditEvent` knopen te lezen. Het queryresultaat is een JSON-object waaruit de bijdragen van de auteur worden geëxtraheerd.

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

Het `JSP` omvat zowel `global.jsp` als `clientlib`.

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

