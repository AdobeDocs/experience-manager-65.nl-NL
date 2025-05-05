---
title: Form Bridge integreren met aangepaste portal voor HTML5-formulieren
description: U kunt de FormBridge-API gebruiken om de waarden van formuliervelden op de pagina HTML op te halen of in te stellen en het formulier te verzenden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 89118bb8-6ec8-4048-b3d6-5c73a9eea33e
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# Form Bridge integreren met aangepaste portal voor HTML5-formulieren{#integrating-form-bridge-with-custom-portal-for-html-forms}

FormBridge is een HTML5-API voor formulierbridge waarmee u met een formulier kunt communiceren. Voor de verwijzing FormBridge API, zie [ FormBridge API verwijzing ](/help/forms/using/form-bridge-apis.md).

U kunt de FormBridge-API gebruiken om de waarden van formuliervelden op de pagina HTML op te halen of in te stellen en het formulier te verzenden. U kunt bijvoorbeeld de API gebruiken om een wizards-achtige ervaring op te bouwen.

Een bestaande HTML-toepassing kan de FormBridge API gebruiken om te communiceren met een formulier en dit in te sluiten in de HTML-pagina. U kunt de volgende stappen gebruiken om de waarde van een veld in te stellen met Form Bridge API.

## HTML5-formulieren integreren in een webpagina {#integrating-html-forms-to-a-web-page}

1. **kies een Profiel of creeer een Profiel**

   1. Navigeer in de CRX DE-interface naar: `https://'[server]:[port]'/crx/de` .
   1. Meld u aan met beheerdersreferenties.
   1. Maak een profiel of kies een bestaand profiel.

      Voor details op hoe te om een profiel tot stand te brengen, zie [ Creërend een Profiel ](/help/forms/using/custom-profile.md).

1. **wijzig het Profiel van de HTML**

   Neem XFA-runtime, XFA-bibliotheek en XFA-formulierfragment op in de profielrenderer, ontwerp uw webpagina en plaats het formulier in de webpagina.

   U kunt bijvoorbeeld het volgende codefragment gebruiken om een app met twee invoervelden en een formulier te maken om de interactie tussen het formulier en een externe app aan te tonen.

   ```xml
   <%@ page session="false"
                  contentType="text/html; charset=utf-8"%><%
   %><%@ taglib prefix="cq" uri="https://www.day.com/taglibs/cq/1.0" %><%
   %><!DOCTYPE html>
   <html manifest="${param.offlineSpec}">
       <head>
          <cq:include script="formRuntime.jsp"/>
           <!-- Portal Scripts and Styles -->
          <cq:include script="portalheader.jsp"/>
       </head>
       <body>
           <div id="leftdiv" >
               <div id="leftdivcontentarea">
                   <!-- Portal Body -->
                 <cq:include script="portalbody.jsp"/>
               </div>
           </div>
           <div id="rightdiv">
               <div id="formBody">
               <cq:include script="config.jsp"/>
               <!-- Form body -->
               <cq:include script="formBody.jsp"/>
               <!  --To assist in page transitions -- add navigation, based on scrolling -->
               <cq:include  script="../nav/scroll/nav_footer.jsp"/>
               <cq:include script="footer.jsp"/>
               </div>
           </div>
       </body>
   </html>
   ```

   >[!NOTE]
   >
   >**lijn 9**, bevat extra verwijzing JSP voor CSS stijlen en de dossiers van JavaScript om de pagina te ontwerpen.
   >
   >
   >De &lt;div id= &quot;rightdiv&quot;> markering op **lijn 18** bevat het fragment van HTML van de vorm XFA.
   >
   >
   >De pagina wordt gestileerd in twee containers: **verlaten** en **juist**. De juiste container heeft het formulier. De linkercontainer heeft twee invoervelden en een deel van de externe HTML-pagina.
   >
   >
   >De volgende schermafbeelding laat zien hoe het formulier in een browser wordt weergegeven.

   ![ portaal ](assets/portal.jpg)

   De linkerkant is een deel van de **pagina van de HTML**. De juiste kant die de gebieden bevat is de **xfa vorm**.

1. **Toegang hebbend tot de vormgebieden van de pagina**

   Hier volgt een voorbeeldscript dat u kunt toevoegen om waarden in een formulierveld in te stellen.

   Bijvoorbeeld, als u **EmployeeName** wilt plaatsen gebruikend de waarden op de Voornaam van Gebieden **&#x200B;**&#x200B;en **Familienaam**, roep de {**functie 6} window.formBridge.setFieldValue.**

   Op dezelfde manier kunt u de waarde lezen door **window.formBridge.getFieldValue** API te roepen.

   ```javascript
   $(function() {
               $(".input").blur(function() {
                   window.formBridge.setFieldValue(
                               'xfa.form.form1.#subform[0].EmployeeName',
                                $("#lname").val()+' '+$("#fname").val()
                              )
                   });
           });
   ```
