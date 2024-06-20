---
title: AEM Forms-werkruimtecomponenten integreren in webtoepassingen
description: Uitleg over het hergebruik van AEM Forms-werkruimtecomponenten in uw eigen webapps voor het gebruik van functionaliteit en verregaande integratie.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: bb4a500d-c34f-4586-83f0-ad7ef69b4fb1
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms, Adaptive Forms
role: Admin, User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# AEM Forms-werkruimtecomponenten integreren in webtoepassingen {#integrating-aem-forms-workspace-components-in-web-applications}

U kunt de AEM Forms-werkruimte gebruiken [componenten](/help/forms/using/description-reusable-components.md) in uw eigen webtoepassing. De volgende voorbeeldimplementatie gebruikt componenten van een AEM Forms-werkruimtendev-pakket dat op een CRX™-instantie is geïnstalleerd om een webtoepassing te maken. Pas de onderstaande oplossing aan uw specifieke behoeften aan. De voorbeeldimplementatie wordt opnieuw gebruikt `UserInfo`, `FilterList`, en `TaskList`in een webportal.

1. Aanmelden bij CRXDE Lite-omgeving `https://'[server]:[port]'/lc/crx/de/`. Zorg ervoor dat u een AEM Forms-ontwikkelpakket voor werkruimten hebt geïnstalleerd.
1. Een pad maken `/apps/sampleApplication/wscomponents`.
1. CSS, afbeeldingen, js/libs, js/runtime en js/registry.js kopiëren

   * Van `/libs/ws`
   * tot `/apps/sampleApplication/wscomponents`.

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

1. Een knooppunt onder /content op naam maken `sampleApplication` en type `nt:unstructured`. In de eigenschappen van dit knooppunt voegt u `sling:resourceType` van het type String en value `sampleApplication`. Voeg in de lijst Toegangsbeheer van dit knooppunt een item toe voor `PERM_WORKSPACE_USER` jcr:lezenrechten toestaan. Ook in de lijst Toegangsbeheer van `/apps/sampleApplication` een item toevoegen voor `PERM_WORKSPACE_USER` jcr:lezenrechten toestaan.
1. In `/apps/sampleApplication/wscomponents/js/registry.js` paden bijwerken van `/lc/libs/ws/` tot `/lc/apps/sampleApplication/wscomponents/` voor sjabloonwaarden.
1. In uw portal kunt u JSP-bestand op `/apps/sampleApplication/GET.jsp`voegt u de volgende code toe om de vereiste componenten in het portaal op te nemen.

   ```jsp
   <script data-main="/lc/apps/sampleApplication/wscomponents/js/demomain" src="/lc/apps/sampleApplication/wscomponents/js/libs/require/require.js"></script>
   <div class="UserInfoView gcomponent" data-name="userinfo"></div>
   <div class="filterListView gcomponent" data-name="filterlist"></div>
   <div class="taskListView gcomponent" data-name="tasklist"></div>
   ```

   Neem ook de CSS-bestanden op die vereist zijn voor de AEM Forms-werkruimtecomponenten.

   >[!NOTE]
   >
   >Elke component wordt toegevoegd aan de componenttag (met klassecomponent) tijdens het renderen. Zorg ervoor dat de homepage deze tags bevat. Zie de `html.jsp` bestand van de AEM Forms-werkruimte voor meer informatie over deze basisturing-tags.

1. Als u de componenten wilt aanpassen, kunt u de bestaande weergaven voor de vereiste component als volgt uitbreiden:

   ```javascript
   define([
       'jquery',
       'underscore',
       'backbone',
       'runtime/views/userinfo'],
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

1. Wijzig portaal CSS om de lay-out, het plaatsen, en de stijl van de vereiste componenten op uw portaal te vormen. U wilt bijvoorbeeld de achtergrondkleur zwart houden voor dit portaal om de component userInfo goed te kunnen bekijken. U kunt dit doen door de achtergrondkleur te wijzigen in `/apps/sampleApplication/wscomponents/css/style.css` als volgt:

   ```css
   body {
       font-family: "Myriad pro", Arial;
       background: #000;    //This was origianlly #CCC
       position: relative;
       margin: 0 auto;
   }
   ```
