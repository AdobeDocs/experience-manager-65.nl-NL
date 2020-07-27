---
title: De landinstelling van de gebruikersinterface van de werkruimte AEM Forms wijzigen
seo-title: De landinstelling van de gebruikersinterface van de werkruimte AEM Forms wijzigen
description: Hoe te om de werkruimte van AEM Forms te wijzigen om tekst, samengevouwen categorieën, rijen, en processen, en de datumkiezer op de interface te lokaliseren.
seo-description: Hoe te om de werkruimte van AEM Forms te wijzigen om tekst, samengevouwen categorieën, rijen, en processen, en de datumkiezer op de interface te lokaliseren.
uuid: c89ff150-a36e-45cc-99a6-8768dbe58eab
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 89f9d666-28e2-4201-8467-ae90693ca5d2
docset: aem65
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---


# De landinstelling van de gebruikersinterface van de werkruimte AEM Forms wijzigen{#changing-the-locale-of-aem-forms-workspace-user-interface}

De werkruimte van AEM Forms biedt uit de box ondersteuning voor Engelse, Franse, Duitse en Japanse talen. Het biedt ook de mogelijkheid om de gebruikersinterface van de werkruimte AEM Forms te lokaliseren naar een andere taal.

U kunt als volgt de gebruikersinterface van de werkruimte AEM Forms lokaliseren naar de taal van uw keuze:

* Tekst van de werkruimte AEM Forms lokaliseren.
* U kunt samengevouwen categorieën, wachtrijen en processen lokaliseren.
* Datumkiezer lokaliseren

Voordat u de bovenstaande stappen uitvoert, moet u de stappen volgen die in de [algemene stappen voor het aanpassen](../../forms/using/generic-steps-html-workspace-customization.md)van de werkruimte van AEM Forms worden vermeld.

>[!NOTE]
>
>Zie [Een nieuw aanmeldingsscherm](../../forms/using/creating-new-login-screen.md)maken als u de taal van het aanmeldingsscherm van de werkruimte AEM Forms wilt wijzigen.

## Tekst lokaliseren {#localizing-text}

Voer de volgende stappen uit om ondersteuning voor een taal *Nieuw* en de landinstellingscode van de browser *nu* toe te voegen.

1. Meld u aan bij CRXDE Lite.
De standaard-URL van CRXDE Lite is `https://'[server]:[port]'/lc/crx/de/index.jsp`.
1. Navigeer naar de locatie `apps/ws/locales` en maak een nieuwe map `nw.`
1. Kopieer het bestand `translation.json`van de locatie `/apps/ws/locales/en-US` naar de locatie `/apps/ws/locales/nw` .
1. Navigeer naar `/apps/ws/locales/nw` en open `translation.json` voor bewerking. Wijzig de landinstelling in het bestand translatie.json.

   De volgende voorbeelden bevatten het bestand translatie.json voor Engelse en Franse landinstellingen van de werkruimte AEM Forms.

   ![translatie_json_in_en](assets/translation_json_in_en.png) ![translatie_json_in_fr](assets/translation_json_in_fr.png)

## Samengevouwen categorieën, wachtrijen en processen lokaliseren {#localizing-collapsed-categories-queues-and-processes}

In de werkruimte AEM Forms worden afbeeldingen gebruikt om kopteksten van categorieën, rijen en processen weer te geven. U hebt ontwikkelingspakket nodig om deze koppen te lokaliseren. Zie [Werkruimtecode maken voor meer informatie over het maken van ontwikkelingspakket.](introduction-customizing-html-workspace.md#building-html-workspace-code)

In de volgende stappen wordt aangenomen dat de nieuwe gelokaliseerde afbeeldingsbestanden *Categories_nw.png*, *Queue_nw.png* en *Processes_nw.png* zijn. De aanbevolen breedte van de afbeeldingen is 19 px.

>[!NOTE]
>
>U kunt als volgt de landinstellingscode van de browser voor de taal vinden. Open `https://'[server]:[port]'/lc/libs/ws/Locale.html`.

![samenvouwen_deelvensters_afbeelding](assets/collapsing_panels_image.png)

Voer de volgende stappen uit om de afbeeldingen te lokaliseren:

1. Plaats de afbeeldingsbestanden met een WebDAV-client in de map */apps/ws/images* .
1. Navigeer naar */apps/ws/css*. Open *newStyle.css* voor bewerking en voeg de volgende items toe:

   ```css
   #categoryListBar .content.nw {
        background: #3e3e3e url(../images/Categories_nw.png) no-repeat 10px 10px;
    }
   
   #filterListBar .content.nw {
       background: #3e3e3e url(../images/Queues_nw.png) no-repeat 10px 10px;
   }
   
   #processNameListBar .content.nw {
       background: #3e3e3e url(../images/Processes_nw.png) no-repeat 10px 10px;
   }
   ```

1. Voer alle semantische veranderingen uit die in het artikel van de Aanpassing van de [Werkruimte](../../forms/using/introduction-customizing-html-workspace.md) worden vermeld.
1. Navigeer naar de map *js/runtime/utility* en open het bestand *usersessie.js* voor bewerking.
1. Zoek de code in het oorspronkelijke codeblok en voeg voorwaarde *lang toe!== &#39;nw&#39;* aan de instructie if:

   ```javascript
   // Orignal code
   setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

   ```javascript
   //new code
    setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP' && lang !== 'nw')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

## Datumkiezer lokaliseren {#localizing-date-picker}

U hebt ontwikkelingspakket nodig om de *datepicker* -API te lokaliseren. Voor gedetailleerde informatie over het creëren van ontwikkelingspakket, zie de code [van de](introduction-customizing-html-workspace.md#building-html-workspace-code)Werkruimte van AEM Forms van de Bouwstijl.

1. Download en extraheer het [jQuery UI-pakket](https://jqueryui.com/download/all/), navigeer naar *&lt;extracted jquery UI package>*\jquery-ui-1.10.2.zip\jquery-ui-1.10.2\ui\i18n.
1. Kopieer het bestand jquery.ui.datepicker-nw.js voor de landinstellingscode nu naar apps/ws/js/libs/jqueryui en breng specifieke wijzigingen voor de landinstelling aan in het bestand.
1. Navigeer naar `apps/ws/js` en open het `jquery.ui.datepicker-nw.js` bestand om het te bewerken.
1. Maak in het bestand main.js een alias voor `jquery.ui.datepicker-nw.js.` De code waarmee een alias voor het `jquery.ui.datepicker-nw.js` bestand wordt gemaakt:

   ```javascript
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. Gebruik alias `jqueryuidatepickernw` om het `jquery.ui.datepicker-nw.js` bestand op te nemen in alle bestanden die datepicker gebruiken. De datepicker wordt gebruikt in de volgende bestanden:

   * `js/runtime/views/outofoffice.js`
   * `js/runtime/views/searchtemplatedetails.js`

   De voorbeeldcode hieronder laat zien hoe u de vermelding jquery.ui.datepicker-nw.js toevoegt:

   ```json
   //Original Code
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, slimScroll, UserSearch, LogManager, Logger) {
   ```

   ```json
   // Code with Date Picker alias for new language
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'jqueryuidatepickernw', // Date Picker alias
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, jQueryUIDatePickerNW, slimScroll, UserSearch, LogManager, Logger) {
   ```

1. Wijzig de standaard datepicker API-instellingen in alle bestanden die de datepicker API gebruiken. De datepicker-API wordt gebruikt in de volgende bestanden:

   * apps\ws\js\runtime\views\searchtemplatedetails.js
   * apps\ws\js\runtime\views\outofoffice.js

   Wijzig de volgende code om de nieuwe landinstelling toe te voegen:

   ```javascript
   if (locale === 'ja-JP') {
      $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
      $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
      $.datepicker.setDefaults($.datepicker.regional.fr);
   } else {
      $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```

   ```javascript
   if (locale === 'ja-JP') {
       $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
       $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
       $.datepicker.setDefaults($.datepicker.regional.fr);
   } else if (locale === 'nw') {
       $.datepicker.setDefaults($.datepicker.regional.nw);
   } else {
       $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```
