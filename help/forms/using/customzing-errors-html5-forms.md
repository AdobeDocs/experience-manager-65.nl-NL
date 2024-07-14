---
title: Foutberichten voor HTML5-formulieren aanpassen
description: Leer hoe u de weergave van foutberichten voor HTML5-formulieren kunt aanpassen, inclusief hoe u de positie en weergave van deze formulieren kunt wijzigen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
feature: HTML5 Forms,Mobile Forms
exl-id: c4ae53a3-8de1-4985-a73e-829749de9814
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Foutberichten voor HTML5-formulieren aanpassen {#customizing-error-messages-for-html-forms}

In HTML5-formulieren wordt de fout alleen voor een geselecteerd veld weergegeven. Er wordt slechts één fout weergegeven. Dit is niet het geval in het vak, de foutberichten en waarschuwingen hebben een vaste positie en een vaste weergave (lettertype en kleur).

Het artikel bevat de stappen voor het aanpassen van foutberichten voor HTML5-formulieren, zodat u het volgende kunt doen:

* de weergave en positie van foutberichten wijzigen. U kunt een fout maken die boven, onder en rechts van een veld wordt weergegeven.
* foutberichten weergeven voor meerdere velden op een bepaald moment.
* geeft de fout weer, ongeacht of een veld is geselecteerd of niet.

## Foutberichten aanpassen  {#customizing-error-messages-nbsp}

Download en extraheer het bijgevoegde pakket (CustomErrorManager-1.0-SNAPSHOT.zip) voordat u de foutberichten aanpast.

Nadat u het pakket hebt uitgepakt, opent u de map CustomErrorManager-1.0-SNAPSHOT. Het bevat de mappen jcr_root en META-INF. Deze mappen bevatten de CSS- en JS-bestanden die nodig zijn om het foutbericht aan te passen.

[Bestand ophalen](assets/customerrormanager-1.0-snapshot.zip)

### De positie van foutberichten aanpassen  {#customizing-the-position-of-error-messages-nbsp}

Als u de positie van het foutbericht wilt aanpassen, voegt u een &lt;div>-tag toe voor elk fout- en waarschuwingsveld, plaatst u de tag &lt;div> links of rechts en past u CSS-stijlen toe op de tag &lt;div>. Voor gedetailleerde stappen, zie de hieronder vermelde procedure:

1. Navigeer naar de map `CustomErrorManager-1.0-SNAPSHOT` en open de map `etc\clientlibs\mf-custom-error-manager\CustomErrorManager\javascript` .
1. Open het `customErrorManager.js` -bestand om het te bewerken. De functie `markError` in het bestand accepteert de volgende parameters:

   |   |  |
   |---|---|
   | jqWidget | jqWidget is de greep voor een widget. |
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
1. Navigeer naar de map `CustomErrorManager-1.0-SNAPSHOT` en maak een archief van de mappen jcr_root en META-INF. Wijzig de naam van het archief in CustomErrorManager-1.0-SNAPSHOT.zip.
1. Gebruik Pakketbeheer om het pakket te uploaden en te installeren.

## Foutberichten weergeven voor meerdere velden  {#display-error-messages-for-multiple-fields-nbsp}

Gebruik het bijgevoegde pakket om foutberichten voor alle velden tegelijk weer te geven. Gebruik het standaardprofiel om één foutbericht weer te geven.

### De weergave van foutberichten aanpassen.  {#customizing-the-appearance-of-error-messages-nbsp}

1. Ga naar de map etc\clientlibs\mf-custom-error-manager\CustomErrorManager\css.

1. Open het bestand sample.css voor bewerking. Het CSS-bestand bevat 2 id&#39;s - #customError, #customWarning. U kunt deze id&#39;s gebruiken om verschillende eigenschappen, zoals kleur en tekengrootte, te wijzigen.

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
1. Gebruik Pakketbeheer om het pakket te uploaden en te installeren.

## Het formulier weergeven met het nieuwe profiel.  {#render-the-form-with-the-new-profile-nbsp}

HTML5-formulieren gebruiken een standaardprofiel uit het vak: `https://&lt;server&gt;/content/xfaforms/profiles/default.html?contentRoot=&lt;xdp location&gt;&template=&lt;name of the xdp&gt;`

Als u een formulier wilt weergeven met de aangepaste foutberichten, geeft u het formulier weer met het foutprofiel: `https://&lt;server&gt;/content/xfaforms/profiles/error.html?contentRoot=&lt;xdp location&gt;&template=&lt;name of the xdp&gt;`

>[!NOTE]
>
>Het bijgevoegde pakket installeert het foutprofiel.
