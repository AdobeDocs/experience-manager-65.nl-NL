---
title: Een aangepaste Cloud Service maken
description: De standaardset Clouden Services kan worden uitgebreid met aangepaste Cloud Servicen
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 9414c77a-b180-4440-8386-e6eb4426e475
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Een aangepaste Cloud Service maken{#creating-a-custom-cloud-service}

De standaardset Clouden Services kan worden uitgebreid met aangepaste Cloud Servicen. Hiermee kunt u aangepaste opmaakcodes op gestructureerde wijze in de pagina injecteren. Dit is vooral handig voor externe analyseproviders, zoals Googles Analytics, Chartmaatbedrijven, enzovoort. Cloud Servicen worden overgeërfd van bovenliggende pagina&#39;s naar onderliggende pagina&#39;s, waarbij de overerving op elk niveau kan worden verbroken.

>[!NOTE]
>
>Deze stapsgewijze handleiding voor het maken van een Cloud Service is een voorbeeld van het gebruik van Googles Analytics. Alles is mogelijk niet van toepassing op het gebruik.

1. Maak in CRXDE Lite een knooppunt onder `/apps` :

   * **Naam**: `acs`
   * **Type**: `nt:folder`

1. Een knooppunt maken onder `/apps/acs` :

   * **Naam**: `analytics`
   * **Type**: `sling:Folder`

1. Maak twee knooppunten onder `/apps/acs/analytics` :

   * **Naam**: componenten
   * **Type**: `sling:Folder`

   en

   * **Naam**: malplaatjes
   * **Type**: `sling:Folder`

1. Klik met de rechtermuisknop `/apps/acs/analytics/components` . Selecteer **creeer...** door **wordt gevolgd creeer Component...** de dialoog die opent laat u specificeren:

   * **Etiket**: `googleanalyticspage`
   * **Titel**: `Google Analytics Page`
   * **Super Type**: `cq/cloudserviceconfigs/components/configpage`
   * **Groep**: `.hidden`

1. Klik **daarna** tweemaal en specificeer:

   * **Toegestane Ouders:** `acs/analytics/templates/googleanalytics`

   Klik **daarna** tweemaal en klik **O.K.**.

1. Een eigenschap toevoegen aan `googleanalyticspage` :

   * **Naam:** `cq:defaultView`
   * **Waarde:** `html`

1. Maak een bestand met de naam `content.jsp` onder `/apps/acs/analytics/components/googleanalyticspage` , met de volgende inhoud:

   ```xml
   <%@page contentType="text/html"
               pageEncoding="utf-8"%><%
   %><%@include file="/libs/foundation/global.jsp"%><div>
   
   <div>
       <h3>Google Analytics Settings</h3>
       <ul>
           <li><div class="li-bullet"><strong>accountID: </strong><br><%= xssAPI.encodeForHTML(properties.get("accountID", "")) %></div></li>
       </ul>
   </div>
   ```

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/` :

   * **Naam**: `dialog`
   * **Type**: `cq:Dialog`
   * **Eigenschappen**:

      * **Naam**: `title`
      * **Type**: `String`
      * **Waarde**: `Google Analytics Config`
      * **Naam**: `xtype`
      * **Type**: `String`
      * **Waarde**: `dialog`

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog` :

   * **Naam**: `items`
   * **Type**: `cq:Widget`
   * **Eigenschappen**:

      * **Naam**: `xtype`
      * **Type**: `String`
      * **Waarde**: `tabpanel`

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog/items` :

   * **Naam**: `items`
   * **Type**: `cq:WidgetCollection`

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items` :

   * **Naam**: tab1
   * **Type**: `cq:Panel`
   * **Eigenschappen**:

      * **Naam**: `title`
      * **Type**: `String`
      * **Waarde**: `Config`

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items/tab1` :

   * **Naam**: punten
   * **Type**: `nt:unstructured`
   * **Eigenschappen**:

      * **Naam**: `fieldLabel`
      * **Type**: Koord
      * **Waarde**: identiteitskaart van de Rekening

      * **Naam**: `fieldDescription`
      * **Type**: `String`
      * **Waarde**: `The account ID assigned by Google. Usually in the form UA-NNNNNN-N`

      * **Naam**: `name`
      * **Type**: `String`
      * **Waarde**: `./accountID`
      * **Naam**: `validateOnBlur`
      * **Type**: `String`
      * **Waarde**: `true`
      * **Naam**: `xtype`
      * **Type**: `String`
      * **Waarde**: `textfield`

1. Kopieer `/libs/cq/cloudserviceconfigs/components/configpage/body.jsp` naar `/apps/acs/analytics/components/googleanalyticspage/body.jsp` en wijzig `libs` naar `apps` op regel 34 en maak van de scriptverwijzing op regel 79 een volledig gekwalificeerd pad.
1. Een sjabloon maken onder `/apps/acs/analytics/templates/` :

   * met **Type van Middel** = `acs/analytics/components/googleanalyticspage`
   * met **Etiket** = `googleanalytics`
   * met **Titel**= `Google Analytics Configuration`
   * met **allowedPath** = `/etc/cloudservices/googleanalytics(/.*)?`
   * met **allowedChildren** = `/apps/acs/analytics/templates/googleanalytics`
   * met **sling:resourceSuperType** = `cq/cloudserviceconfigs/templates/configpage` (op malplaatjeknoop, niet jcr:inhoudsknoop)
   * met **cq:designPath** = `/etc/designs/cloudservices/googleanalytics` (op jcr:content)

1. Maak een component: `/apps/acs/analytics/components/googleanalytics`.

   Voeg de volgende inhoud toe aan `googleanalytics.jsp` :

   ```xml
   <%@page import="org.apache.sling.api.resource.Resource,
                   org.apache.sling.api.resource.ValueMap,
                   org.apache.sling.api.resource.ResourceUtil,
                   com.day.cq.wcm.webservicesupport.Configuration,
                   com.day.cq.wcm.webservicesupport.ConfigurationManager" %>
   <%@include file="/libs/foundation/global.jsp" %><%
   
   String[] services = pageProperties.getInherited("cq:cloudserviceconfigs", new String[]{});
   ConfigurationManager cfgMgr = resource.getResourceResolver().adaptTo(ConfigurationManager.class);
   if(cfgMgr != null) {
       String accountID = null;
       Configuration cfg = cfgMgr.getConfiguration("googleanalytics", services);
       if(cfg != null) {
           accountID = cfg.get("accountID", null);
       }
   
       if(accountID != null) {
       %>
   <script type="text/javascript">
   
     var _gaq = _gaq || [];
     _gaq.push(['_setAccount', '<%= accountID %>']);
     _gaq.push(['_trackPageview']);
   
     (function() {
       var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
       ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'https://www') + '.google-analytics.com/ga.js';
       var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
     })();
   
   </script><%
       }
   }
   %>
   ```

   Dit zou de douanemarkering moeten uitvoeren die op de configuratieeigenschappen wordt gebaseerd.

1. Navigeer naar `http://localhost:4502/miscadmin#/etc/cloudservices` en maak een pagina:

   * **Titel**: `Google Analytics`
   * **Naam**: `googleanalytics`

   Ga terug in CRXDE Lite en voeg onder `/etc/cloudservices/googleanalytics` de volgende eigenschap toe aan `jcr:content` :

   * **Naam**: `componentReference`
   * **Type**: `String`
   * **Waarde**: `acs/analytics/components/googleanalytics`

1. Navigeer aan de pas gecreëerde pagina van de Dienst ( `http://localhost:4502/etc/cloudservices/googleanalytics.html`) en klik **+** om tot een config te leiden:

   * **de Configuratie van de Ouder**: `/etc/cloudservices/googleanalytics`
   * **Titel:** `My First GA Config`

   Kies **Configuratie van Googles Analytics** en klik **creeer**.

1. Ga een **identiteitskaart van de Rekening** in, bijvoorbeeld, `AA-11111111-1`. Klik **OK**.
1. Navigeer aan een pagina en voeg de onlangs gecreeerde configuratie in de paginaeigenschappen, onder de **Cloud Servicen** tabel toe.
1. Aan de pagina wordt de aangepaste markering toegevoegd.
