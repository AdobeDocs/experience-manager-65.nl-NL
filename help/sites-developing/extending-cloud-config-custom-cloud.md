---
title: Een aangepaste Cloud Service maken
description: De standaardset Clouden Services kan worden uitgebreid met aangepaste Cloud Servicen
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 9414c77a-b180-4440-8386-e6eb4426e475
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Een aangepaste Cloud Service maken{#creating-a-custom-cloud-service}

De standaardset Clouden Services kan worden uitgebreid met aangepaste Cloud Servicen. Hiermee kunt u aangepaste opmaakcodes op gestructureerde wijze in de pagina injecteren. Dit is vooral handig voor externe analyseproviders, zoals Googles Analytics, Chartmaatbedrijven, enzovoort. Cloud Servicen worden overgeërfd van bovenliggende pagina&#39;s naar onderliggende pagina&#39;s, waarbij de overerving op elk niveau kan worden verbroken.

>[!NOTE]
>
>Deze stapsgewijze handleiding voor het maken van een Cloud Service is een voorbeeld van het gebruik van Googles Analytics. Alles is mogelijk niet van toepassing op het gebruik.

1. In CRXDE Lite maakt u een knooppunt onder `/apps`:

   * **Naam**: `acs`
   * **Type**: `nt:folder`

1. Een knooppunt maken onder `/apps/acs`:

   * **Naam**: `analytics`
   * **Type**: `sling:Folder`

1. Twee knooppunten maken onder `/apps/acs/analytics`:

   * **Naam**: componenten
   * **Type**: `sling:Folder`

   en

   * **Naam**: sjablonen
   * **Type**: `sling:Folder`

1. Klikken met rechtermuisknop `/apps/acs/analytics/components`. Selecteren **Maken...** gevolgd door **Component maken...** In het dialoogvenster dat wordt geopend, kunt u het volgende opgeven:

   * **Label**: `googleanalyticspage`
   * **Titel**: `Google Analytics Page`
   * **Supertype**: `cq/cloudserviceconfigs/components/configpage`
   * **Groep**: `.hidden`

1. Klikken **Volgende** twee keer en geef aan:

   * **Toegestane bovenliggende elementen:** `acs/analytics/templates/googleanalytics`

   Klikken **Volgende** twee keer en klik **OK**.

1. Een eigenschap toevoegen aan `googleanalyticspage`:

   * **Naam:** `cq:defaultView`
   * **Waarde:** `html`

1. Een bestand met de naam `content.jsp` krachtens `/apps/acs/analytics/components/googleanalyticspage`, met de volgende inhoud:

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

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/`:

   * **Naam**: `dialog`
   * **Type**: `cq:Dialog`
   * **Eigenschappen**:

      * **Naam**: `title`
      * **Type**: `String`
      * **Waarde**: `Google Analytics Config`
      * **Naam**: `xtype`
      * **Type**: `String`
      * **Waarde**: `dialog`

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog`:

   * **Naam**: `items`
   * **Type**: `cq:Widget`
   * **Eigenschappen**:

      * **Naam**: `xtype`
      * **Type**: `String`
      * **Waarde**: `tabpanel`

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog/items`:

   * **Naam**: `items`
   * **Type**: `cq:WidgetCollection`

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items`:

   * **Naam**: tab1
   * **Type**: `cq:Panel`
   * **Eigenschappen**:

      * **Naam**: `title`
      * **Type**: `String`
      * **Waarde**: `Config`

1. Een knooppunt maken onder `/apps/acs/analytics/components/googleanalyticspage/dialog/items/items/tab1`:

   * **Naam**: items
   * **Type**: `nt:unstructured`
   * **Eigenschappen**:

      * **Naam**: `fieldLabel`
      * **Type**: String
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

1. Kopiëren `/libs/cq/cloudserviceconfigs/components/configpage/body.jsp` tot `/apps/acs/analytics/components/googleanalyticspage/body.jsp` en wijzigen `libs` tot `apps` op regel 34 en maak van de scriptverwijzing op regel 79 een volledig gekwalificeerd pad.
1. Een sjabloon maken onder `/apps/acs/analytics/templates/`:

   * with **Resourcetype** = `acs/analytics/components/googleanalyticspage`
   * with **Label** = `googleanalytics`
   * with **Titel**= `Google Analytics Configuration`
   * with **allowedPath** = `/etc/cloudservices/googleanalytics(/.*)?`
   * with **allowedChildren** = `/apps/acs/analytics/templates/googleanalytics`
   * with **sling:resourceSuperType** = `cq/cloudserviceconfigs/templates/configpage` (op sjabloonknooppunt, niet op het knooppunt jcr:content)
   * with **cq:designPath** = `/etc/designs/cloudservices/googleanalytics` (op jcr:content)

1. Een component maken: `/apps/acs/analytics/components/googleanalytics`.

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

1. Navigeren naar `http://localhost:4502/miscadmin#/etc/cloudservices` en maak een pagina:

   * **Titel**: `Google Analytics`
   * **Naam**: `googleanalytics`

   Ga terug in CRXDE Lite en onder `/etc/cloudservices/googleanalytics`, voegt u de volgende eigenschap toe aan `jcr:content`:

   * **Naam**: `componentReference`
   * **Type**: `String`
   * **Waarde**: `acs/analytics/components/googleanalytics`

1. Navigeer aan de pas gecreëerde pagina van de Dienst ( `http://localhost:4502/etc/cloudservices/googleanalytics.html`) en klik op de knop **+** om een config te creëren:

   * **Bovenliggende configuratie**: `/etc/cloudservices/googleanalytics`
   * **Titel:**  `My First GA Config`

   Kies **Configuratie Googles Analytics** en klik op **Maken**.

1. Voer een **Account-id**, bijvoorbeeld `AA-11111111-1`. Klikken **OK**.
1. Navigeer naar een pagina en voeg de nieuw gemaakte configuratie toe in de pagina-eigenschappen, onder de **Cloud Servicen** tab.
1. Aan de pagina wordt de aangepaste markering toegevoegd.
