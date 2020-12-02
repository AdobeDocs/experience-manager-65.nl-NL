---
title: FormulierBridge integreren met aangepaste portal voor HTML5-formulieren
seo-title: FormulierBridge integreren met aangepaste portal voor HTML5-formulieren
description: Met de FormBridge-API kunt u de waarden van formuliervelden ophalen of instellen vanaf de HTML-pagina en het formulier verzenden.
seo-description: Met de FormBridge-API kunt u de waarden van formuliervelden ophalen of instellen vanaf de HTML-pagina en het formulier verzenden.
uuid: c8911f82-1a25-47a5-9a06-19b5dce74a2c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: bd9bf095-d74d-458c-afe7-fab04050849d
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# FormulierBridge integreren met aangepaste portal voor HTML5-formulieren{#integrating-form-bridge-with-custom-portal-for-html-forms}

FormBridge is een bridge-API voor HTML5-formulieren waarmee u kunt werken met een formulier. Zie [Referentie FormBridge API](/help/forms/using/form-bridge-apis.md) voor de API-referentie van FormBridge.

Met de FormBridge-API kunt u de waarden van formuliervelden ophalen of instellen vanaf de HTML-pagina en het formulier verzenden. U kunt bijvoorbeeld de API gebruiken om een wizards-achtige ervaring op te bouwen.

Een bestaande HTML-toepassing kan de FormBridge API gebruiken om te communiceren met een formulier en dit in te sluiten in de HTML-pagina. U kunt de volgende stappen gebruiken om de waarde van een veld in te stellen met de API van Form Bridge.

## HTML5-formulieren integreren in een webpagina {#integrating-html-forms-to-a-web-page}

1. **Een profiel kiezen of een profiel maken**

   1. In de interface CRX DE, navigeer aan: `https://'[server]:[port]'/crx/de`.
   1. Meld u aan met beheerdersreferenties.
   1. Maak een profiel of kies een bestaand profiel.

      Zie [Een nieuw profiel maken](/help/forms/using/custom-profile.md) voor meer informatie over het maken van een profiel.

1. **Het HTML-profiel wijzigen**

   Neem XFA-runtime, XFA-bibliotheek en XFA-formulier-HTML-fragment op in de profielrenderer, ontwerp uw webpagina en plaats het formulier in de webpagina.

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
   >De **regel 9** bevat aanvullende JSP-verwijzing voor CSS-stijlen en JavaScript-bestanden om de pagina te ontwerpen.
   >
   >
   >De &lt;div id=&quot;rightdiv&quot;>-tag op **regel 18** bevat het HTML-fragment van het XFA-formulier.
   De pagina wordt opgemaakt in twee containers: **left** en **right**. De juiste container heeft het formulier. De linkercontainer heeft twee invoervelden en een deel van de externe HTML-pagina.
   De volgende schermafbeelding laat zien hoe het formulier in een browser wordt weergegeven.

   ![portaal](assets/portal.jpg)

   De linkerzijde is een onderdeel van de **HTML-pagina**. De rechterzijde met de velden is het **xfa-formulier**.

1. **De formuliervelden openen vanaf de pagina**

   Hier volgt een voorbeeldscript dat u kunt toevoegen om waarden in een formulierveld in te stellen.

   Als u bijvoorbeeld **EmployeeName** wilt instellen met de waarden in de velden **Voornaam** en **Achternaam**, roept u de functie **window.formBridge.setFieldValue** aan.

   Op dezelfde manier kunt u de waarde lezen door de API **window.formBridge.getFieldValue** aan te roepen.

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
