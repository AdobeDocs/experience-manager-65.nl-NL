---
title: De zoekfunctionaliteit van Adobe Experience Manager-middelen uitbreiden
description: Breid de zoekmogelijkheden van Adobe Experience Manager-middelen uit tot meer dan de standaardwaarden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 15%

---


# Zoeken naar elementen uitbreiden {#extending-assets-search}

U kunt de [!DNL Adobe Experience Manager Assets] zoekmogelijkheden uitbreiden. Hiermee zoekt u elementen op tekenreeksen uit het vak. [!DNL Experience Manager Assets]

Het zoeken wordt gedaan via de interface QueryBuilder zodat kan het onderzoek met verscheidene predikaten worden aangepast. U kunt de standaardset voorspelden in de volgende map bedekken: `/apps/dam/content/search/searchpanel/facets`.

U kunt ook extra tabbladen toevoegen aan het deelvenster [!DNL Assets] Beheer.

>[!CAUTION]
>
>Vanaf [!DNL Experience Manager] 6.4 is de klassieke gebruikersinterface afgekeurd. Voor aankondiging, zie [afgekeurde en verwijderde eigenschappen](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/deprecated-removed-features.html). Adobe raadt u aan een interface met aanraakbediening te gebruiken. Zie [zoekfacetten](/help/assets/search-facets.md)voor informatie over aanpassingen.

## Bedekking {#overlaying}

Om de pre-gevormde voorspelden te bedekken, kopieer de `facets` knoop van `/libs/dam/content/search/searchpanel` aan `/apps/dam/content/search/searchpanel/` of specificeer een ander `facetURL` bezit in de `searchpanel` configuratie (het gebrek is aan `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json`).

![screen_shot_2012-06-05at113619am](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>Standaard bestaat de mappenstructuur onder / `apps` niet en moet deze worden gemaakt. Zorg ervoor dat de knooppunttypen overeenkomen met de knooppunttypen onder / `libs`.

## Tabs toevoegen {#adding-tabs}

U kunt extra zoektabbladen toevoegen door deze in de beheerinterface voor middelen te configureren. Extra tabbladen maken:

1. Maak de mapstructuur `/apps/wcm/core/content/damadmin/tabs,`als deze nog niet bestaat en kopieer het `tabs` knooppunt van `/libs/wcm/core/content/damadmin` en plak het.
1. Maak en configureer het tweede tabblad naar wens.

   >[!NOTE]
   >
   >Wanneer u een tweede bestand maakt, moet u een `siteadminsearchpanel``id` eigenschap instellen om formulierconflicten te voorkomen.

## Aangepaste voorspelling maken {#creating-custom-predicates}

[!DNL Assets] wordt geleverd met een set vooraf gedefinieerde voorspelling die kan worden gebruikt om een pagina voor het delen van elementen aan te passen. Het aanpassen van een Aandeel van Activa op deze manier wordt behandeld in [creeer en vorm een pagina](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page)van het Aandeel van Activa.

Naast het gebruiken van reeds bestaande predikaten, kunnen de ontwikkelaars van de Manager van de Ervaring hun eigen predikaten ook creëren gebruikend de [Bouwer van de Vraag API](/help/sites-developing/querybuilder-api.md).

Voor het maken van aangepaste predikaten is basiskennis van het [Widget-framework](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html)vereist.

De beste praktijken moeten een bestaand predikaat kopiëren en het aanpassen. Voorspelregels voor voorbeelden bevinden zich in **/libs/cq/search/components/predicates**.

### Voorbeeld: Een eenvoudige voorspelling van eigenschappen maken {#example-build-a-simple-property-predicate}

Een voorspelling van eigenschappen maken:

1. Maak een componentmap in de projectmap, bijvoorbeeld **/apps/geometrixx/components/titlepreate**.
1. Add **content.xml**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Title Predicate"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Toevoegen `titlepredicate.jsp`.

   ```java
   <%--
   
     Sample title predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Title</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:title";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // createId adds a counter to the predicate name - useful in case this predicate
           // is inserted multiple times on the same page.
           var id = qb.createId(predicateName);
   
           // Hidden field that defines the property to search for; in our case this
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property" etc.)
           // indicates the server to use the property predicate
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id,
               "value": propertyName
           });
   
           // The visible text field. The name has to be like the one of the hidden field above
           // plus the ".value" suffix.
           qb.addField({
               "xtype": "textfield",
               "renderTo": elemId,
               "name": id + ".value"
           });
   
           // Depending on the predicate additional parameters allow to configure the
           // predicate. Here we add an operation parameter to create a "like" query.
           // Again note the name set to the id and a suffix.
           qb.addField({
               "xtype": "hidden",
               "renderTo": elemId,
               "name": id + ".operation",
               "value": "like"
           });
       });
   </script>
   ```

1. Als u de component beschikbaar wilt maken, moet u deze kunnen bewerken. Als u een component bewerkbaar wilt maken in CRXDE, voegt u een knooppunt **cq:editConfig** van het primaire type **cq:EditConfig** toe. U kunt alinea&#39;s verwijderen door een eigenschap met meerdere waarden **cq:actions** met één waarde van **DELETE** toe te voegen.
1. Navigeer naar de browser en schakel op de voorbeeldpagina (bijvoorbeeld **press.html**) de ontwerpmodus in en schakel de nieuwe component in voor het alineasysteem &#39;prediken&#39; (bijvoorbeeld **links**).

1. In de modus **Bewerken** is de nieuwe component nu beschikbaar in de assistent (in de groep **Zoeken** ). Voeg de component in de kolom **Voorspelden** in en typ een zoekwoord, bijvoorbeeld **Ruitje** , en klik op het vergrootglas om de zoekopdracht te starten.

   >[!NOTE]
   >
   >Zorg er bij het zoeken voor dat u de term exact typt, inclusief het juiste hoofdlettergebruik.

### Voorbeeld: Een eenvoudige groepspreiding maken {#example-build-a-simple-group-predicate}

Om een groep te bouwen predikaat:

1. Maak een componentmap in de projectmap, bijvoorbeeld **/apps/geometrixx/components/picspredicate.**
1. Add **content.xml**:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0" xmlns:cq="https://www.day.com/jcr/cq/1.0" xmlns:jcr="https://www.jcp.org/jcr/1.0"
       jcr:primaryType="cq:Component"
       jcr:title="Image Formats"
       sling:resourceSuperType="foundation/components/parbase"
       allowedParents="[*/parsys]"
       componentGroup="Search"/>
   ```

1. Voeg **titlePredicate.jsp** toe:

   ```java
   <%--
   
     Sample group predicate component
   
   --%><%@ page import="java.util.Calendar" %><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   
       // A unique id is necessary in case this predicate is inserted multiple times on the same page.
       String elemId = "cq-predicate-" +  Long.toString(Calendar.getInstance().getTimeInMillis());
   
   %><div class="predicatebox">
   
       <div class="title">Image Formats</div>
   
       <%-- The wrapper for the form elements. All items will be append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return e.g. "1_group".
           var groupId = qb.createGroupId();
   
           // Hidden field that defines the property to search for  - in our case "dc:format" -
           // and declares the group of predicates. "property" in the name ("1_group.property")
           // indicates to the server to use the "property predicate"
           // (com.day.cq.search.eval.JcrPropertyPredicateEvaluator).
           qb.addField({
               "xtype": "hidden",
               "renderTo": "<%= elemId %>",
               "name": groupId + "." + predicateName, // 1_group.property
               "value": propertyName
           });
   
           // Declare to combine the multiple values using OR.
           qb.add(new CQ.Ext.form.Hidden({
               "name": groupId + ".p.or",  // 1_group.p.or
               "value": "true"
           }));
   
           // The options
           var options = [
               { "label":"JPEG", "value":"image/jpeg"},
               { "label":"PNG",  "value":"image/png" },
               { "label":"GIF",  "value":"image/gif" }
           ];
   
           // Build a checkbox for each option.
           for (var i = 0; i < options.length; i++) {
               qb.addField({
                   "xtype": "checkbox",
                   "renderTo": "<%= elemId %>",
                   // 1_group.property.0_value, 1_group.property.1_value etc.
                   "name": groupId + "." +  predicateName + "." + i + "_value",
                   "inputValue": options[i].value,
                   "boxLabel": options[i].label,
                   "listeners": {
                       "check": function() {
                           // Submit the search form when checking/unchecking a checkbox.
                           qb.submit();
                       }
                   }
               });
           }
       });
   ```

1. Als u de component beschikbaar wilt maken, moet u deze kunnen bewerken. Als u een component bewerkbaar wilt maken in CRXDE, voegt u een knooppunt **cq:editConfig** van het primaire type **cq:EditConfig** toe. U kunt alinea&#39;s verwijderen door een eigenschap met meerdere waarden **cq:actions** met één waarde van **DELETE** toe te voegen.
1. Navigeer naar de browser en schakel op de voorbeeldpagina (bijvoorbeeld **press.html**) de ontwerpmodus in en schakel de nieuwe component in voor het alineasysteem &#39;prediken&#39; (bijvoorbeeld **links**).
1. In de modus **Bewerken** is de nieuwe component nu beschikbaar in de assistent (in de groep **Zoeken** ). Voeg de component in de kolom **Voorspelden** in.

## Vooraf geïnstalleerde widgets {#installed-predicate-widgets}

De volgende voorspelling is beschikbaar als vooraf geconfigureerde ExtJS-widgets.

### FulltextPredicate {#fulltextpredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| predikaatName | Tekenreeks | Naam van de voorspelling. Defaults to `fulltext` |
| searchCallback | -functie | Callback voor het activeren van zoeken op gebeurtenis `keyup`. Defaults to `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| predikaatName | Tekenreeks | Naam van de voorspelling. Defaults to `property` |
| propertyName | Tekenreeks | Naam van de eigenschap JCR. Defaults to `jcr:title` |
| defaultValue | Tekenreeks | Vooraf ingevulde standaardwaarde. |

### PathPredicate {#pathpredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| predikaatName | Tekenreeks | Naam van de voorspelling. Defaults to `path` |
| rootPath | Tekenreeks | Hoofdpad van de voorspelling. Defaults to `/content/dam` |
| pathFieldPredicateName | Tekenreeks | Defaults to `folder` |
| showFlatOption | Boolean | Vlag om Selectievakje weer te geven `search in subfolders`. Heeft als standaardwaarde true. |

### DatePredicate {#datepredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| predikaatName | Tekenreeks | Naam van de voorspelling. Defaults to `daterange` |
| eigenschapsnaam | Tekenreeks | Naam van de eigenschap JCR. Defaults to `jcr:content/jcr:lastModified` |
| defaultValue | Tekenreeks | Vooraf ingevulde standaardwaarde |

### OptionsPredicate {#optionspredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| title | Tekenreeks | Hiermee wordt een extra bovenste titel toegevoegd |
| predikaatName | Tekenreeks | Naam van de voorspelling. Defaults to `daterange` |
| eigenschapsnaam | Tekenreeks | Naam van de eigenschap JCR. Defaults to `jcr:content/metadata/cq:tags` |
| samenvouwen | Tekenreeks | Niveau samenvouwen. Defaults to `level1` |
| triggerSearch | Boolean | Markering voor het activeren van zoekopdrachten bij controle. Standaard ingesteld op false |
| searchCallback | -functie | Callback voor het teweegbrengen van onderzoek. Defaults to `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | Getal | Time-out voordat searchCallback wordt gestart. Wordt standaard ingesteld op 800 ms |

## Zoekresultaten aanpassen {#customizing-search-results}

De presentatie van zoekresultaten op een pagina voor het delen van bedrijfsmiddelen wordt bepaald door de geselecteerde lens. De Elementen van de Manager van de ervaring komen met een reeks vooraf bepaalde lenzen die kunnen worden gebruikt om een pagina van het Aandeel van Activa aan te passen. Op deze manier wordt het op deze manier aanpassen van een Asset Share behandeld in het [maken en configureren van een pagina](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page)voor het delen van bedrijfsmiddelen.

Naast het gebruik van bestaande lenzen kunnen ontwikkelaars van Experience Manager ook hun eigen lenzen maken.
