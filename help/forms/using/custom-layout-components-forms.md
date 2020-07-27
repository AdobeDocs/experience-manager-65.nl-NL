---
title: Aangepaste indelingscomponenten voor aangepaste formulieren maken
seo-title: Aangepaste indelingscomponenten voor aangepaste formulieren maken
description: Procedure voor het maken van aangepaste indelingscomponenten voor adaptieve formulieren.
seo-description: Procedure voor het maken van aangepaste indelingscomponenten voor adaptieve formulieren.
uuid: f0bb5fcd-3938-4804-ad0c-d96d3083fd01
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: d4ae432d-557d-4e89-92b8-dca5f37cb6f8
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# Aangepaste indelingscomponenten voor aangepaste formulieren maken{#creating-custom-layout-components-for-adaptive-forms}

## Vereiste {#prerequisite}

Kennis van lay-outs, waarmee u een aangepaste lay-out kunt maken/gebruiken. Zie Lay-out [van deelvenster](../../forms/using/layout-capabilities-adaptive-forms.md)wijzigen.

## Indelingsonderdeel van deelvenster Adaptief formulier {#adaptive-form-panel-layout-component}

Met de component Indeling van het deelvenster Adaptief formulier bepaalt u hoe adaptieve formuliercomponenten worden ingedeeld in een deelvenster dat relatief is ten opzichte van de gebruikersinterface.

## Een aangepaste deelvensterlay-out maken {#creating-a-custom-panel-layout}

1. Navigeer naar de locatie `/crx/de`.
1. Kopieer een deelvensterlay-out van de locatie `/libs/fd/af/layouts/panel` (bijvoorbeeld `tabbedPanelLayout`) naar `/apps` (bijvoorbeeld `/apps/af-custom-layout`).
1. Wijzig de naam van de layout waarnaar u hebt gekopieerd `customPanelLayout`. Wijzig de eigenschappen van de knooppunten `qtip` en `jcr:description`. Wijzig deze bijvoorbeeld in `Custom layout - Toggle tabs`.

qtip

![Layout CRX DE-momentopname van deelvenster Aangepast](assets/custom_layout_new.png)

>[!NOTE]
>
>Als u de eigenschap instelt `guideComponentType`op de waarde, `fd/af/layouts/panel` bepaalt u dat de indeling een deelvensterindeling is.

1. Wijzig de naam van het bestand `tabbedPanelLayout.jsp` onder de nieuwe indeling in customPanelLayout.jsp.
1. Als u nieuwe stijlen en gedragingen wilt introduceren, maakt u een clientbibliotheek onder het `etc` knooppunt. Maak bijvoorbeeld op de locatie /etc/af-custom-layout-clientlib de client-library van het knooppunt. Laat de knoop het categoriebezit af.panel.custom hebben. Het heeft de volgende .css en .js dossiers:

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

1. Als u de vormgeving en het gedrag wilt verbeteren, kunt u een `client library`pictogram opnemen.

   Werk ook de paden van opgenomen scripts bij in .jsp-bestanden. Werk het `customPanelLayout.jsp` bestand bijvoorbeeld als volgt bij:

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

   Het `/apps/af-custom-layout/customPanelLayout/defaultNavigatorLayout.jsp` bestand:

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

   ![De lay-out Aangepast deelvenster wordt weergegeven in de lay-outlijst](assets/auth-layt.png) van het deelvenster met ![Schermopname van het aangepaste formulier. De lay-out](assets/s1.png) van het deelvenster wordt gebruikt voor een aangepaste ![schermafbeelding die de schakelfunctionaliteit van de aangepaste indeling aangeeft](assets/s2.png)

Voorbeeld-ZIP voor een aangepaste deelvensterindeling en een adaptief formulier dat deze gebruikt.

[Bestand ophalen](assets/af-custom-layout.zip)
