---
title: Componenten van AEM Forms-werkruimten integreren in webtoepassingen
seo-title: Componenten van AEM Forms-werkruimten integreren in webtoepassingen
description: AEM Forms werkruimtecomponenten in uw eigen webapps opnieuw gebruiken om functionaliteit te benutten en verregaande integratie te bieden.
seo-description: AEM Forms werkruimtecomponenten in uw eigen webapps opnieuw gebruiken om functionaliteit te benutten en verregaande integratie te bieden.
uuid: bb9b8aa0-3f41-4f44-8eb7-944e778ee8a6
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 6be87939-007e-42c7-8a41-e34ac2b8bed4
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# Componenten van AEM Forms-werkruimten integreren in webtoepassingen {#integrating-aem-forms-workspace-components-in-web-applications}

U kunt [componenten](/help/forms/using/description-reusable-components.md) van de werkruimte van AEM Forms gebruiken in uw eigen Webtoepassing. De volgende voorbeeldimplementatie gebruikt componenten van een AEM Forms-werkruimte-dev-pakket dat is geïnstalleerd op een CRX™-instantie om een webtoepassing te maken. Pas de onderstaande oplossing aan uw specifieke behoeften aan. De voorbeeldimplementatie hergebruikt `UserInfo`, `FilterList`en `TaskList`componenten binnen een Webportaal.

1. Meld u aan bij de CRXDE Lite-omgeving `https://'[server]:[port]'/lc/crx/de/`. Zorg ervoor dat u een AEM Forms-ontwikkelpakket hebt geïnstalleerd.
1. Maak een pad `/apps/sampleApplication/wscomponents`.
1. CSS, afbeeldingen, js/libs, js/runtime en js/registry.js kopiëren

   * Van `/libs/ws`
   * to `/apps/sampleApplication/wscomponents`.

1. Maak een bestand demomain.js in de map /apps/sampleApplication/wscomponents/js. Kopieer code van /libs/ws/js/main.js naar demomain.js.
1. In demomain.js, verwijder de code om Router te initialiseren en de volgende code toe te voegen:

   ```javascript
   require(['initializer','runtime/util/usersession'],
       function(initializer, UserSession) {
           UserSession.initialize(
               function() {
                   // Render all the global components
                   initializer.initGlobal();
               });
       });
   ```

1. Creeer een knoop onder /content door naam `sampleApplication` en type `nt:unstructured`. Voeg in de eigenschappen van dit knooppunt `sling:resourceType` het type String en value toe `sampleApplication`. Voeg in de lijst Toegangsbeheer van dit knooppunt een item toe voor het `PERM_WORKSPACE_USER` toestaan van jcr:read-bevoegdheden. Ook, in de Lijst van het Toegangsbeheer van `/apps/sampleApplication` `PERM_WORKSPACE_USER` voeg een ingang voor het toestaan van jcr toe:read voorrechten.
1. In `/apps/sampleApplication/wscomponents/js/registry.js` werk wegen van `/lc/libs/ws/` aan `/lc/apps/sampleApplication/wscomponents/` voor malplaatjewaarden bij.
1. In uw portalstartpagina JSP- dossier bij `/apps/sampleApplication/GET.jsp`, voeg de volgende code toe om de vereiste componenten binnen het portaal te omvatten.

   ```jsp
   <script data-main="/lc/apps/sampleApplication/wscomponents/js/demomain" src="/lc/apps/sampleApplication/wscomponents/js/libs/require/require.js"></script>
   <div class="UserInfoView gcomponent" data-name="userinfo"></div>
   <div class="filterListView gcomponent" data-name="filterlist"></div>
   <div class="taskListView gcomponent" data-name="tasklist"></div>
   ```

   Neem ook de CSS-bestanden op die vereist zijn voor de AEM Forms-werkruimtecomponenten.

   >[!NOTE]
   >
   >Elke component wordt toegevoegd aan de componenttag (met klassecomponent) tijdens het renderen. Zorg ervoor dat de homepage deze tags bevat. Zie het `html.jsp` dossier van de werkruimte van AEM Forms om meer over deze markeringen van de basiscontrole te weten te komen.

1. Als u de componenten wilt aanpassen, kunt u de bestaande weergaven voor de vereiste component als volgt uitbreiden:

   ```javascript
   define([
       ‘jquery’,
       ‘underscore’,
       ‘backbone’,
       ‘runtime/views/userinfo'],
       function($, _, Backbone, UserInfo){
           var demoUserInfo = UserInfo.extend({
               //override the functions to customize the functionality
               render: function() {
                   UserInfo.prototype.render.call(this); // call the render function of the super class
                   …
                   //other tasks
                   …
               }
           });
           return demoUserInfo;
   });
   ```

1. Wijzig portaal CSS om de lay-out, het plaatsen, en de stijl van de vereiste componenten op uw portaal te vormen. U wilt bijvoorbeeld de achtergrondkleur zwart houden voor dit portaal om de component userInfo goed te kunnen bekijken. U kunt dit doen door de achtergrondkleur `/apps/sampleApplication/wscomponents/css/style.css` als volgt te wijzigen:

   ```css
   body {
       font-family: "Myriad pro", Arial;
       background: #000;    //This was origianlly #CCC
       position: relative;
       margin: 0 auto;
   }
   ```
