---
title: Een aangepaste Cloud-service maken
seo-title: Een aangepaste Cloud-service maken
description: De standaardset met Cloud Services kan worden uitgebreid met aangepaste Cloud-servicetypen
seo-description: De standaardset met Cloud Services kan worden uitgebreid met aangepaste Cloud-servicetypen
uuid: b105a0c1-b68c-4f57-8e3b-561c8051a08e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: e48e87c6-43ca-45ba-bd6b-d74c969757cd
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Een aangepaste Cloud-service maken{#creating-a-custom-cloud-service}

De standaardset Cloud Services kan worden uitgebreid met aangepaste Cloud Service-typen. Hierdoor kunt u aangepaste opmaakcodes op gestructureerde wijze in de pagina injecteren. Dit is vooral handig voor andere analisten, zoals Google Analytics, Chartbone enzovoort. Cloud Services worden overgeërfd van bovenliggende pagina&#39;s naar onderliggende pagina&#39;s, waarbij de overerving op elk niveau kan worden verbroken.

>[!NOTE]
>
>Deze stapsgewijze handleiding voor het maken van een nieuwe Cloud Service is een voorbeeld met Google Analytics. Alles is mogelijk niet van toepassing op het gebruik.

1. Maak in CRXDE Lite een nieuw knooppunt onder `/apps`:

   * **Naam**: `acs`
   * **Type**: `nt:folder`

1. Een nieuw knooppunt maken onder `/apps/acs`:

   * **Naam**: `analytics`
   * **Type**: `sling:Folder`

1. Twee nieuwe knooppunten maken onder `/apps/acs/analytics`:

   * **Naam**: componenten
   * **Type**: `sling:Folder`
   and

   * **Naam**: sjablonen
   * **Type**: `sling:Folder`


1. Klik met de rechtermuisknop op `/apps/acs/analytics/components`. **** Selecteer **Maken... gevolgd door Component** maken... In het dialoogvenster dat wordt geopend, kunt u het volgende opgeven:

   * **Label**: `googleanalyticspage`
   * **Titel**: `Google Analytics Page`
   * **Supertype**: `cq/cloudserviceconfigs/components/configpage`
   * **Groep**: `.hidden`

1. Klik tweemaal op **Volgende** en geef op:

   * **** Toegestane bovenliggende elementen: `acs/analytics/templates/googleanalytics`
   Klik tweemaal op **Volgende** en klik op **OK**.

1. Een eigenschap toevoegen aan `googleanalyticspage`:

   * **** Naam: `cq:defaultView`
   * **** Waarde: `html`

1. Maak een nieuw bestand met de naam `content.jsp` onder `/apps/acs/analytics/components/googleanalyticspage`, met de volgende inhoud:

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

1. Een nieuw knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/`:

   * **Naam**: `dialog`
   * **Type**: `cq:Dialog`
   * **Eigenschappen**:

      * **Naam**: `title`
      * **Type**: `String`
      * **Waarde**: `Google Analytics Config`
      * **Naam**: `xtype`
      * **Type**: `String`
      * **Waarde**: `dialog`

1. Een nieuw knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog`:

   * **Naam**: `items`
   * **Type**: `cq:Widget`
   * **Eigenschappen**:

      * **Naam**: `xtype`
      * **Type**: `String`
      * **Waarde**: `tabpanel`

1. Een nieuw knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog/items`:

   * **Naam**: `items`
   * **Type**: `cq:WidgetCollection`

1. Een nieuw knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items`:

   * **Naam**: tab1
   * **Type**: `cq:Panel`
   * **Eigenschappen**:

      * **Naam**: `title`
      * **Type**: `String`
      * **Waarde**: `Config`

1. Een nieuw knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items/tab1`:

   * **Naam**: items
   * **Type**: `nt:unstructured`
   * **Eigenschappen**:

      * **Naam**: `fieldLabel`
      * **Type**:String
      * **Waarde**: Account-id

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

1. Kopieer `/libs/cq/cloudserviceconfigs/components/configpage/body.jsp` naar `/apps/acs/analytics/components/googleanalyticspage/body.jsp` en wijzig `libs` naar `apps` regel 34 en maak van de scriptverwijzing op regel 79 een volledig gekwalificeerd pad.
1. Een nieuwe sjabloon maken onder `/apps/acs/analytics/templates/`:

   * met **brontype** = `acs/analytics/components/googleanalyticspage`
   * met **Label** = `googleanalytics`
   * met **Titel**= `Google Analytics Configuration`
   * met **allowedPath** = `/etc/cloudservices/googleanalytics(/.*)?`
   * met **allowedChildren** = `/apps/acs/analytics/templates/googleanalytics`
   * met **sling:resourceSuperType** = `cq/cloudserviceconfigs/templates/configpage` (op sjabloonknooppunt, niet de jcr:content-node)
   * met **cq:designPath** = `/etc/designs/cloudservices/googleanalytics` (op jcr:content)

1. Nieuwe component maken: `/apps/acs/analytics/components/googleanalytics`.

   Voeg de volgende inhoud toe aan `googleanalytics.jsp`:

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

1. Navigeer naar een nieuwe pagina `http://localhost:4502/miscadmin#/etc/cloudservices` en maak deze:

   * **Titel**: `Google Analytics`
   * **Naam**: `googleanalytics`
   Ga terug in CRXDE Lite, en onder `/etc/cloudservices/googleanalytics`, voeg het volgende bezit aan toe `jcr:content`:

   * **Naam**: `componentReference`
   * **Type**: `String`
   * **Waarde**: `acs/analytics/components/googleanalytics`


1. Navigeer aan de pas gecreëerde pagina van de Dienst ( `http://localhost:4502/etc/cloudservices/googleanalytics.html`) en klik **+** om een nieuw config tot stand te brengen:

   * **Bovenliggende configuratie**: `/etc/cloudservices/googleanalytics`
   * **** Titel:  `My First GA Config`
   Kies **Google Analytics Configuration** en klik op **Create**.

1. Voer bijvoorbeeld een **account-id** in `AA-11111111-1`. Click **OK**.
1. Navigeer naar een pagina en voeg de zojuist gemaakte configuratie toe in de pagina-eigenschappen onder het tabblad **Cloud Services** .
1. Aan de pagina wordt de aangepaste markering toegevoegd.

