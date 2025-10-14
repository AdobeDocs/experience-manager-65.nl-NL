---
title: Aangepaste indelingscomponenten voor aangepaste formulieren maken
description: Procedure voor het maken van aangepaste indelingscomponenten voor adaptieve formulieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 544b06f9-2456-4c05-88c2-b5349947742d
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
source-git-commit: 8a77756e8ba771c8de9950c2323bef8f23cc59b4
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Aangepaste indelingscomponenten voor aangepaste formulieren maken{#creating-custom-layout-components-for-adaptive-forms}

## Vereiste {#prerequisite}

Kennis van lay-outs, waarmee u een aangepaste lay-out kunt maken/gebruiken. Zie [&#x200B; Veranderende Lay-out van het Comité &#x200B;](../../forms/using/layout-capabilities-adaptive-forms.md).

## Indelingsonderdeel van deelvenster Adaptief formulier {#adaptive-form-panel-layout-component}

Met de component Indeling van het deelvenster Adaptief formulier bepaalt u hoe adaptieve formuliercomponenten worden ingedeeld in een deelvenster dat relatief is ten opzichte van de gebruikersinterface.

## Een aangepaste deelvensterlay-out maken {#creating-a-custom-panel-layout}

1. Navigeer naar de locatie `/crx/de` .
1. Kopieer een deelvensterlay-out van de locatie `/libs/fd/af/layouts/panel` (bijvoorbeeld `tabbedPanelLayout` ) naar `/apps` (bijvoorbeeld `/apps/af-custom-layout` ).
1. Wijzig de naam van de layout waarnaar u hebt gekopieerd. `customPanelLayout` Wijzig de eigenschappen van de knooppunten `qtip` en `jcr:description` . Wijzig deze bijvoorbeeld in `Custom layout - Toggle tabs` .

qtip

![&#x200B; Lay-out CRX DE Momentopname van het Comité van de Douane &#x200B;](assets/custom_layout_new.png)

>[!NOTE]
>
>Door de eigenschap `guideComponentType` in te stellen op de waarde `fd/af/layouts/panel` bepaalt u dat de lay-out een deelvensterlay-out is.

1. Wijzig de naam van het bestand `tabbedPanelLayout.jsp` onder de nieuwe layout in customPanelLayout.jsp.
1. Als u nieuwe stijlen en gedragingen wilt introduceren, maakt u een clientbibliotheek onder het knooppunt `etc` . Maak bijvoorbeeld op de locatie /etc/af-custom-layout-clientlib de client-library van het knooppunt. Laat de knoop het categoriebezit af.panel.custom hebben. Het heeft de volgende .css en .js dossiers:

   ```css
   /** CSS defining new styles used by custom layout **/
   
   .menu-nav {
       background-color: rgb(198, 38, 76);
       height: 30px;
    width: 30px;
    font-size: 2em;
    color: white;
       -webkit-transition: -webkit-transform 1s;  /* For Safari 3.1 to 6.0 */
    transition: transform 1s;
   }
   
   .tab-content {
    border: 1px solid #08b1cf;
   }
   
   .custom-navigation {
       -webkit-transition: width 1s, height 1s, -webkit-transform 1s;  /* For Safari 3.1 to 6.0 */
    transition: width 1s, height 1s, transform 1s;
   }
   
   .panel-name {
       padding-left: 30px;
       font-size: 20px;
   }
   
   @media (min-width: 992px) {
    .nav-close {
     width: 0px;
       }
   }
   
   @media (min-width: 768px) and (max-width: 991px) {
    .nav-close {
     height: 0px;
       }
   }
   
   @media (max-width: 767px) {
    .menu-nav, .custom-navigation {
        display: none;
       }
   }
   ```

   ```javascript
   /** function for toggling the navigators **/
   var toggleNav = function () {
   
       var nav = $('.custom-navigation');
       if (nav) {
           nav.toggleClass('nav-close');
       }
   }
   
   /** function to populate the panel title **/
   $(window).on('load', function() {
       if (window.guideBridge) {
           window.guideBridge.on("elementNavigationChanged",
           function (evntName, evnt) {
                       var activePanelSom = evnt.newText,
                           activePanel = window.guideBridge._guideView.getView(activePanelSom);
                       $('.panel-name').html(activePanel.$itemNav.find('a').html());
                   }
           );
       }
   });
   ```

1. U kunt een `client library` opnemen om de vormgeving en het gedrag te verbeteren.

   Werk ook de paden van opgenomen scripts bij in .jsp-bestanden. Werk bijvoorbeeld het bestand `customPanelLayout.jsp` als volgt bij:

   ```html
   <%-- jsp encapsulating navigator container and panel container divs --%>
   
   <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
   <cq:includeClientLib categories="af.panel.custom"/>
   <div>
       <div class="row">
           <div class="col-md-2 col-sm-2 hidden-xs menu-nav glyphicon glyphicon-align-justify" onclick="toggleNav();"></div>
           <div class="col-md-10 col-sm-10 hidden-xs panel-name"></div>
       </div>
       <div class="row">
           <div class="col-md-2 hidden-xs guide-tab-stamp-list custom-navigation">
               <cq:include script = "/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp" />
           </div>
           <div  class="col-md-10">
               <c:if test="${fn:length(guidePanel.description) > 0}">
                   <div class="<%=GuideConstants.GUIDE_PANEL_DESCRIPTION%>">
                       ${guide:encodeForHtml(guidePanel.description,xssAPI)}
                           <cq:include script="/libs/fd/af/components/panel/longDescription.jsp"/>
                   </div>
               </c:if>
               <cq:include script = "/apps/af-custom-layout/customPanelLayout/panelContainer.jsp"/>
           </div>
       </div>
   </div>
   ```

   Het `/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp` -bestand:

   ```html
   <%-- jsp governing the navigation part --%>
   
   <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
   <%@ page import="com.adobe.aemds.guide.utils.StyleUtils" %>
   <%-- navigation tabs --%>
   <ul id="${guidePanel.id}_guide-item-nav-container" class="tab-navigators tab-navigators-vertical in"
       data-guide-panel-edit="reorderItems" role="tablist">
       <c:forEach items="${guidePanel.items}" var="panelItem">
           <c:set var="isNestedLayout" value="${guide:hasNestablePanelLayout(guidePanel,panelItem)}"/>
           <li id="${panelItem.id}_guide-item-nav" title="${guide:encodeForHtmlAttr(panelItem.navTitle,xssAPI)}" data-path="${panelItem.path}" role="tab" aria-controls="${panelItem.id}_guide-item">
               <c:set var="panelItemCss" value="${panelItem.cssClassName}"/>
               <% String panelItemCss = (String) pageContext.getAttribute("panelItemCss");%>
               <a data-guide-toggle="tab" class="<%= StyleUtils.addPostfixToClasses(panelItemCss, "_nav") %> guideNavIcon nested_${isNestedLayout}">${guide:encodeForHtml(panelItem.navTitle,xssAPI)}</a>
               <c:if test="${isNestedLayout}">
                   <guide:initializeBean name="guidePanel" className="com.adobe.aemds.guide.common.GuidePanel"
                       resourcePath="${panelItem.path}" restoreOnExit="true">
                       <sling:include path="${panelItem.path}"
                                      resourceType="/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp"/>
                   </guide:initializeBean>
               </c:if>
               <em></em>
           </li>
       </c:forEach>
   </ul>
   ```

   De bijgewerkte `/apps/af-custom-layout/customPanelLayout/panelContainer.jsp`:

   ```html
   <%-- jsp governing the panel content --%>
   
   <%@include file="/libs/fd/af/components/guidesglobal.jsp"%>
   
   <div id="${guidePanel.id}_guide-item-container" class="tab-content">
       <c:if test="${guidePanel.hasToolbar && (guidePanel.toolbarPosition == 'Top') }">
           <sling:include path="${guidePanel.toolbar.path}"/>
       </c:if>
   
   <c:forEach items="${guidePanel.items}" var="panelItem">
       <div class="tab-pane" id="${panelItem.id}_guide-item" role="tabpanel">
           <c:set var="isNestedLayout" value="${guide:hasNestablePanelLayout(guidePanel,panelItem)}"/>
           <c:if test="${isNestedLayout}">
               <c:set var="guidePanelResourceType" value="/apps/af-custom-layout/customPanelLayout/panelContainer.jsp" scope="request"/>
           </c:if>
           <sling:include path="${panelItem.path}" resourceType="${panelItem.resourceType}"/>
       </div>
   </c:forEach>
   <c:if test="${guidePanel.hasToolbar && (guidePanel.toolbarPosition == 'Bottom')}">
       <sling:include path="${guidePanel.toolbar.path}"/>
   </c:if>
   </div>
   ```

1. Open een adaptief formulier in de ontwerpmodus. De door u gedefinieerde deelvensterlay-out wordt toegevoegd aan de lijst voor het configureren van deelvensterlay-outs.

   ![&#x200B; de lay-out van het Comité van de Douane toont omhoog in de lijst van de paneellay-out &#x200B;](assets/auth-layt.png) ![&#x200B; Schermschot van adaptieve vorm, gebruikend de lay-out van het douanepaneel &#x200B;](assets/s1.png) ![&#x200B; het tonen van knevelfunctionaliteit van de douanelay-out &#x200B;](assets/s2.png)

Voorbeeld-ZIP voor een aangepaste deelvensterindeling en een adaptief formulier dat deze gebruikt.

[Bestand ophalen](assets/af-custom-layout.zip)
