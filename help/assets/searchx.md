---
title: Zoekfunctionaliteit uitbreiden
description: Breid de onderzoeksmogelijkheden van  [!DNL Adobe Experience Manager Assets]  voorbij de gebreken uit.
contentOwner: AG
role: Developer
feature: Search
exl-id: 9e33d1c0-232b-458a-ad6a-f595aa541a5a
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 12%

---

# Zoeken naar elementen uitbreiden {#extending-assets-search}

U kunt de zoekmogelijkheden van [!DNL Adobe Experience Manager Assets] uitbreiden. In het vak zoekt [!DNL Experience Manager Assets] naar elementen op tekenreeksen.

Het zoeken wordt gedaan via de interface QueryBuilder zodat kan het onderzoek met verscheidene predikaten worden aangepast. U kunt de standaardset voorspelden in de volgende map bedekken: `/apps/dam/content/search/searchpanel/facets` .

U kunt ook extra tabbladen toevoegen aan het deelvenster [!DNL Assets] Beheer.

>[!CAUTION]
>
>Vanaf [!DNL Experience Manager] 6.4 is de klassieke gebruikersinterface afgekeurd. Adobe raadt u aan een interface met aanraakbediening te gebruiken. Voor aanpassing, zie [&#x200B; onderzoeksfacetten &#x200B;](/help/assets/search-facets.md).

## Bedekking {#overlaying}

Als u de vooraf geconfigureerde voorspelling wilt bedekken, kopieert u de node `facets` van `/libs/dam/content/search/searchpanel` naar `/apps/dam/content/search/searchpanel/` of geeft u een andere eigenschap `facetURL` op in de configuratie `searchpanel` (de standaardwaarde is `/libs/dam/content/search/searchpanel/facets.overlay.infinity.json` ).

![&#x200B; screen_shot_2012-06-05at113619am &#x200B;](assets/screen_shot_2012-06-05at113619am.png)

>[!NOTE]
>
>Standaard bestaat de mapstructuur onder `/apps` niet, zodat u deze kunt maken. Zorg ervoor dat de knooppunttypen overeenkomen met de knooppunttypen onder `/libs` .

## Tabs toevoegen {#adding-tabs}

U kunt extra zoektabbladen toevoegen door deze te configureren in de beheerinterface van [!DNL Assets] . Extra tabbladen maken:

1. Maak de mapstructuur `/apps/wcm/core/content/damadmin/tabs,` als deze nog niet bestaat, en kopieer het knooppunt `tabs` van `/libs/wcm/core/content/damadmin` en plak het.
1. Maak en configureer het tweede tabblad naar wens.

   >[!NOTE]
   >
   >Wanneer u een tweede `siteadminsearchpanel` maakt, moet u de eigenschap `id` zo instellen dat formulierconflicten worden voorkomen.

## Aangepaste voorspelling maken {#creating-custom-predicates}

[!DNL Assets] wordt geleverd met een set vooraf gedefinieerde voorspelling die kan worden gebruikt om een pagina voor het delen van elementen aan te passen. Het aanpassen van een Aandeel van Activa op deze manier wordt behandeld in [&#x200B; creeer en vorm een pagina van het Aandeel van Activa &#x200B;](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Naast het gebruiken van reeds bestaande predikaten, [!DNL Experience Manager] kunnen de ontwikkelaars hun eigen predikaten ook creëren gebruikend [&#x200B; de Bouwer van de Vraag API &#x200B;](/help/sites-developing/querybuilder-api.md).

Het creëren van douane voorspelt vereist basiskennis over het [&#x200B; kader Widgets &#x200B;](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html).

De beste praktijken moeten een bestaand predikaat kopiëren en het aanpassen. Voorspelregels voor voorbeelden vindt u in **/libs/cq/search/components/predicates** .

### Voorbeeld: een eenvoudige eigenschap maken {#example-build-a-simple-property-predicate}

Een voorspelling van eigenschappen maken:

1. Maak een componentmap in de projectmap, bijvoorbeeld **/apps/weretail/components/titlepreate** .
1. Voeg **content.xml** toe:

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
   
       <%-- The wrapper for the form elements. All items are appended to this wrapper. --%>
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
           // is the "dc:title" metadata. The name "property" (or "1_property", "2_property", and so on.)
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
   
           // Depending on the predicate, additional parameters let you configure the
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
1. Navigeer aan uw browser, en op uw steekproefpagina (bijvoorbeeld, **press.html**) schakelaar aan ontwerpwijze en laat uw nieuwe component voor het predikaat paragraafsysteem (bijvoorbeeld, **verlaten**) toe.

1. Op **geef** wijze uit, is de nieuwe component nu beschikbaar in sidekick (die in de **wordt gevonden 3&rbrace; groep van het Onderzoek &lbrace;).** Tussenvoegsel de component in **voorspelt** kolom en typ een onderzoekswoord, bijvoorbeeld, **Ruitje** en klik het vergrootglas om het onderzoek te beginnen.

   >[!NOTE]
   >
   >Zorg er bij het zoeken voor dat u de term exact typt, inclusief het juiste hoofdlettergebruik.

### Voorbeeld: een eenvoudige groepspreiding maken {#example-build-a-simple-group-predicate}

Om een groep te bouwen predikaat:

1. Creeer een componentenomslag in uw projectfolder, bijvoorbeeld, **/apps/weretail/components/picspredicate**.
1. Voeg **content.xml** toe:

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
   
       <%-- The wrapper for the form elements. All items are append to this wrapper. --%>
       <div id="<%= elemId %>" class="content"></div>
   
   </div><script type="text/javascript">
   
       CQ.Ext.onLoad(function() {
   
           var predicateName = "property";
           var propertyName = "jcr:content/metadata/dc:format";
           var elemId = "<%= elemId %>";
   
           // Get the page wide available QueryBuilder.
           var qb = CQ.search.Util.getQueryBuilder();
   
           // Create a unique group ID; will return for example, "1_group".
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
                   // 1_group.property.0_value, 1_group.property.1_value, and so on.
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
1. Navigeer aan uw browser, en op uw steekproefpagina (bijvoorbeeld, **press.html**) schakelaar aan ontwerpwijze en laat uw nieuwe component voor het predikaat paragraafsysteem (bijvoorbeeld, **verlaten**) toe.
1. Op **geef** wijze uit, is de nieuwe component nu beschikbaar in sidekick (die in de **wordt gevonden 3&rbrace; groep van het Onderzoek &lbrace;).** Tussenvoegsel de component in de **Predicates** kolom.

## Vooraf geïnstalleerde widgets {#installed-predicate-widgets}

De volgende voorspelling is beschikbaar als vooraf geconfigureerde ExtJS-widgets.

### FulltextPredicate {#fulltextpredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| predikaatName | String | Naam van de voorspelling. Heeft als standaardwaarde `fulltext` |
| searchCallback | Functie | Callback voor het activeren van zoeken op gebeurtenis `keyup` . Heeft als standaardwaarde `CQ.wcm.SiteAdmin.doSearch` |

### PropertyPredicate {#propertypredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| predikaatName | String | Naam van de voorspelling. Heeft als standaardwaarde `property` |
| propertyName | String | Naam van de eigenschap JCR. Heeft als standaardwaarde `jcr:title` |
| defaultValue | String | Vooraf ingevulde standaardwaarde. |

### PathPredicate {#pathpredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| predikaatName | String | Naam van de voorspelling. Heeft als standaardwaarde `path` |
| rootPath | String | Hoofdpad van de voorspelling. Heeft als standaardwaarde `/content/dam` |
| pathFieldPredicateName | String | Heeft als standaardwaarde `folder` |
| showFlatOption | Boolean | Vlag om Selectievakje weer te geven `search in subfolders`. Heeft als standaardwaarde true. |

### DatePredicate {#datepredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| predikaatName | String | Naam van de voorspelling. Heeft als standaardwaarde `daterange` |
| eigenschapsnaam | String | Naam van de eigenschap JCR. Heeft als standaardwaarde `jcr:content/jcr:lastModified` |
| defaultValue | String | Vooraf ingevulde standaardwaarde |

### OptionsPredicate {#optionspredicate}

| Eigenschap | Type | Beschrijving |
|---|---|---|
| titel | String | Hiermee wordt een extra bovenste titel toegevoegd |
| predikaatName | String | Naam van de voorspelling. Heeft als standaardwaarde `daterange` |
| eigenschapsnaam | String | Naam van de eigenschap JCR. Heeft als standaardwaarde `jcr:content/metadata/cq:tags` |
| ineenstorten | String | Niveau samenvouwen. Heeft als standaardwaarde `level1` |
| triggerSearch | Boolean | Markering voor het activeren van zoekopdrachten bij controle. Standaard ingesteld op false |
| searchCallback | Functie | Callback voor het teweegbrengen van onderzoek. Heeft als standaardwaarde `CQ.wcm.SiteAdmin.doSearch` |
| searchTimeoutTime | Getal | Time-out voordat searchCallback wordt gestart. Wordt standaard ingesteld op 800 ms |

## Zoekresultaten aanpassen {#customizing-search-results}

De presentatie van zoekresultaten op een pagina voor het delen van bedrijfsmiddelen wordt bepaald door de geselecteerde lens. [!DNL Experience Manager Assets] wordt geleverd met een set vooraf gedefinieerde lenzen die kunnen worden gebruikt om een pagina voor het delen van elementen aan te passen. Het aanpassen van een Aandeel van Activa op deze manier wordt behandeld in [&#x200B; Creërend en Vormend een Pagina van het Aandeel van Activa &#x200B;](/help/assets/assets-finder-editor.md#creating-and-configuring-an-asset-share-page).

Naast het gebruik van reeds bestaande lenzen kunnen ontwikkelaars van [!DNL Experience Manager] ook hun eigen lenzen maken.
