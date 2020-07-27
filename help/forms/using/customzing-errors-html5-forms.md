---
title: Foutberichten voor HTML5-formulieren aanpassen
seo-title: Foutberichten voor HTML5-formulieren aanpassen
description: Leer hoe u de weergave van foutberichten voor HTML5-formulieren kunt aanpassen, inclusief hoe u de positie en weergave van deze berichten kunt wijzigen.
seo-description: Leer hoe u de weergave van foutberichten voor HTML5-formulieren kunt aanpassen, inclusief hoe u de positie en weergave van deze berichten kunt wijzigen.
uuid: 6f48b64e-858f-4323-ad50-88e25f3c2e3d
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 44e49789-9075-41b3-bce8-03e8efce2d5a
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---


# Foutberichten voor HTML5-formulieren aanpassen {#customizing-error-messages-for-html-forms}

In HTML5-formulieren hebben foutberichten en -waarschuwingen een vaste positie en weergave (font en color). De fout wordt alleen voor een geselecteerd veld weergegeven en er wordt slechts één fout weergegeven.

Het artikel bevat de stappen waarmee u foutberichten voor HTML5-formulieren kunt aanpassen aan

* de weergave en positie van foutberichten wijzigen. U kunt een fout maken die boven, onder en rechts van een veld wordt weergegeven.
* foutberichten weergeven voor meerdere velden op een bepaald moment.
* geeft de fout weer ongeacht of een veld is geselecteerd of niet.

## Foutberichten aanpassen  {#customizing-error-messages-nbsp}

Download en extraheer het bijgevoegde pakket (CustomErrorManager-1.0-SNAPSHOT.zip) voordat u de foutberichten aanpast.

Nadat u het pakket hebt uitgepakt, opent u de map CustomErrorManager-1.0-SNAPSHOT. Het bevat de mappen jcr_root en META-INF. Deze mappen bevatten de CSS- en JS-bestanden die nodig zijn om het foutbericht aan te passen.

[Bestand ophalen](assets/customerrormanager-1.0-snapshot.zip)

### De positie van foutberichten aanpassen  {#customizing-the-position-of-error-messages-nbsp}

Als u de positie van het foutbericht wilt aanpassen, voegt u &lt;div>-tag toe voor elk fout- en waarschuwingsveld, plaatst u de tag &lt;div> links of rechts en past u CSS-stijlen toe op de tag &lt;div>. Voor gedetailleerde stappen, zie de hieronder vermelde procedure:

1. Navigeer naar de `CustomErrorManager-1.0-SNAPSHOT`map en open de `etc\clientlibs\mf-custom-error-manager\CustomErrorManager\javascript` map.
1. Open het `customErrorManager.js` bestand om het te bewerken. De `markError` functie in het bestand accepteert de volgende parameters:

   |  |  |
   |---|---|
   | jqWidget | jqWidget is de greep voor widget. |
   | msg | bevat het foutbericht |
   | type | geeft aan of het een fout of een waarschuwing betreft |

1. Bij de implementatie buiten het vak worden aan de rechterkant van het veld foutberichten weergegeven. Gebruik de volgende code om de foutberichten bovenaan weer te geven.

   ```javascript
   markError: function (jqWidget, msg, type) {
               var element = jqWidget.element,                                //Gives the div containing widget
                   pos = $(element).offset(),                          //Calculates the position of the div in the view port
                                                                   msgHeight = xfalib.view.util.TextMetrics.measureExtent(msg).height + 5;  //Calculating the height of the Error Message
                   styles = {};
                   styles.left = pos.left + "px";         // Assign the desired left position using pos.left. Here it is calculated for exact left of the field
                   styles.top = pos.top - msgHeight + "px";  // Assign the desired top position using pos.top. Here it is calculated for top of the field
               if (type != "warning") {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the warning div if it is not present already
                       jqWidget.errorDiv=$("<div id='customError'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the warning div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               } else {
                   if(!jqWidget.errorDiv){
                                                                                   //Adding the error div if it is not present already
                       jqWidget.errorDiv=$("<div id='customWarning'></div>").appendTo('body');
                   }
                   jqWidget.$css(jqWidget.errorDiv.get(0), styles); // Applying the styles to the error div
                   jqWidget.errorDiv.text(msg).show();                     //Showing the warning message
               }
   
           },
   ```

1. Sla het bestand op en sluit het.
1. Navigeer naar de `CustomErrorManager-1.0-SNAPSHOT` map en maak een archief van de mappen jcr_root en META-INF. Wijzig de naam van het archief in CustomErrorManager-1.0-SNAPSHOT.zip.
1. Gebruik pakketbeheer om het pakket te uploaden en te installeren.

## Foutberichten weergeven voor meerdere velden  {#display-error-messages-for-multiple-fields-nbsp}

Gebruik het bijgevoegde pakket om foutberichten voor alle velden tegelijk weer te geven. Gebruik het standaardprofiel als u één foutbericht wilt weergeven.

### De weergave van foutberichten aanpassen.  {#customizing-the-appearance-of-error-messages-nbsp}

1. Ga naar etc\clientlibs\mf-custom-error-manager\CustomErrorManager\css folder.

1. Open het bestand sample.css voor bewerking.Het CSS-bestand bevat 2 id&#39;s- #customError, #customWarning. U kunt deze id&#39;s gebruiken om verschillende eigenschappen te wijzigen, zoals kleur, tekengrootte, enz.

   Gebruik de volgende code om de tekengrootte en kleur van fout-/waarschuwingsberichten te wijzigen.

   ```css
   #customError {
   color: #0000FF; // it changes the color of Error Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 24px;  // it changes the font size of Error Message
   z-index:5;
   }
   
   #customWarning {
   color: #00FF00;  // it changes the color of Warning Message
   display:none;
   position:absolute;
   opacity:0.85;
   font-size: 18px;   // it changes the font size of Warning Message
   z-index:5;
   }
   
   Save the changes.
   ```

1. Sla het bestand op en sluit het.
1. Navigeer naar de map CustomErrorManager-1.0-SNAPSHOT en maak een archief van de mappen jcr_root en META-INF. Wijzig de naam van het archief in CustomErrorManager-1.0-SNAPSHOT.zip.
1. Gebruik pakketbeheer om het pakket te uploaden en te installeren.

## Het formulier weergeven met het nieuwe profiel.  {#render-the-form-with-the-new-profile-nbsp}

HTML5-formulieren gebruiken een standaardprofiel uit het vak: https://&lt;server>/content/xfaforms/profiles/default.html?contentRoot=&lt;xdp location>&amp;template=&lt;name of the xdp>

Als u een formulier wilt weergeven met de aangepaste foutberichten, geeft u het formulier weer met het foutprofiel: https://&lt;server>/content/xfaforms/profiles/error.html?contentRoot=&lt;xdp location>&amp;template=&lt;name of the xdp>

>[!NOTE]
>
>Het bijgevoegde pakket installeert het foutprofiel.

