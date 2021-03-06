---
title: Voorbeeld van UI-moduletypen van ContextHub
seo-title: Voorbeeld van UI-moduletypen van ContextHub
description: ContextHub verstrekt verscheidene modules van steekproefUI die u in uw oplossingen kunt gebruiken
seo-description: ContextHub verstrekt verscheidene modules van steekproefUI die u in uw oplossingen kunt gebruiken
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
translation-type: tm+mt
source-git-commit: a8ba56849f6bb9f0cf6571fc51f4b5cae71620e0
workflow-type: tm+mt
source-wordcount: '1194'
ht-degree: 0%

---


# Sample ContextHub UI-moduletypen {#sample-contexthub-ui-module-types}

ContextHub verstrekt verscheidene modules van steekproefUI die u in uw oplossingen kunt gebruiken. De volgende informatie wordt verstrekt:

* De belangrijkste eigenschappen van de module UI.
* Waar u de broncode kunt vinden, zodat u deze kunt openen voor leerdoeleinden.
* Hoe te om de module UI te vormen.

Voor informatie over het toevoegen van modules UI aan ContextHub, zie [het Toevoegen van een Module UI](ch-configuring.md#adding-a-ui-module). Voor informatie over het ontwikkelen van modules UI, zie [Creërend de Moduletypes van de Module ContextHub](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

## Contextthub.base UI-moduletype {#contexthub-base-ui-module-type}

Het contexthub.base moduletype UI is het basistype voor alle andere UI moduletypes. Als dusdanig verstrekt het generische eigenschappen voor het teruggeven van opslaggegevens.

De volgende functies zijn beschikbaar:

* **Titel en pictogram:** Geef een titel op voor de gebruikersinterface-module en een pictogram. Naar het pictogram kan worden verwezen met een URL of vanuit de pictogrambibliotheek van de Koral UI.
* **Gegevens opslaan:één of meer opslaglocaties** identificeren waaruit gegevens moeten worden opgehaald.
* **Inhoud:** specificeer de inhoud die in de module UI verschijnt aangezien het in de toolbar ContextHub verschijnt.
* **Popover-inhoud:** geef de inhoud op die in een pop-up wordt weergegeven wanneer op de gebruikersinterface wordt geklikt of er op wordt getikt.
* **Modus Volledig scherm:** bepalen of de modus Volledig scherm is toegestaan.

De broncode bevindt zich in /libs/granite/contexthub/code/ui/container/js/ContextHub.UI.BaseModuleRenderer.js.

### Configuratie {#configuration}

Configureer de module contexthub.base UI met behulp van een Javascript-object in JSON-indeling. Omvat om het even welke volgende eigenschappen om de eigenschappen van de UI module te vormen:

* **afbeelding:** Een URL naar een afbeelding die als pictogram moet worden weergegeven.
* **pictogram:** De naam van een  [Koral UI-](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html) iconklasse. Als u een waarde opgeeft voor zowel het pictogram als de afbeeldingseigenschappen, wordt de afbeelding gebruikt.

* **titel:** Een titel voor de module UI. De titel wordt weergegeven wanneer de aanwijzer op het pictogram van de gebruikersinterface wordt gepauzeerd.
* **fullscreen:** Een booleaanse waarde die aangeeft of de UI-module de modus Volledig scherm ondersteunt. Gebruik `true` om volledig scherm en `false` te steunen om volledige het schermwijze te verhinderen.

* **sjabloon:** Een  [](https://handlebarsjs.com/) Handlebarstemplate die de inhoud specificeert die in de toolbar ContextHub moet teruggeven. Gebruik maximaal twee `<p>`-tags.

* **storeMapping:** een sleutel/archieftoewijzing. Gebruik de sleutel in malplaatjes Handlebar om tot de bijbehorende ContextHub opslaggegevens toegang te hebben.
* **lijst:** Een array van items die als een lijst in een pop-up moeten worden weergegeven wanneer op de gebruikersinterface wordt geklikt. Als u dit item opneemt, neemt u geen popoverTemplate op. De waarde is een array van objecten met de volgende toetsen:

   * titel: De tekst die voor dit item moet worden weergegeven
   * afbeelding: (Optioneel) Een URL naar een afbeelding die links moet worden weergegeven
   * pictogram: (Optioneel) Een CUI-pictogramklasse die links moet worden weergegeven. genegeerd als een afbeelding is opgegeven
   * geselecteerd: (Optioneel) Een Booleaanse waarde die aangeeft of dit item moet worden weergegeven als geselecteerd (true=selected). Geselecteerde items worden standaard weergegeven met een vet lettertype. Gebruik een eigenschap `listType` om andere weergaven te configureren (zie hieronder).

* **listType:** De stijl die moet worden gebruikt voor items in de keuzelijst. Gebruik een van de volgende waarden:

   * vinkje
   * selectievakje
   * radio

* **popoverTemplate:** Een malplaatje van Handlebars dat de inhoud specificeert in popover terug te geven wanneer de module UI wordt geklikt. Als u dit item opneemt, moet u het `list`-item niet opnemen.

### Voorbeeld {#example}

In het volgende voorbeeld wordt een contexthub.base UI-module geconfigureerd voor het weergeven van informatie uit een [contexthub.emulators](/help/sites-developing/ch-samplestores.md#granite-emulators-sample-store-candidate)-winkel. Het `template` punt toont aan hoe te om gegevens uit de opslag te verkrijgen door de sleutel te gebruiken die `storeMapping` punt vestigt.

```xml
{
   "icon": "coral-Icon--move",
    "title": "Screen Resolution",
    "storeMapping": {
      "emulator": "emulators"
    },
    "template": "<p>{{{ i18n \"Resolution\"}}}</p><p>{{{emulator.currentDevice.width}}} x {{{emulator.currentDevice.height}}}</p>"
}
```

![chlimage_1-76](assets/chlimage_1-76a.png)

## contexthub.browserinfo UI Module Type {#contexthub-browserinfo-ui-module-type}

In de UI-module contextthub.browserinfo wordt informatie over de webbrowser en het besturingssysteem van de client weergegeven. De informatie wordt verkregen van de surferinfo store, die op [contexthub.surferinfo](/help/sites-developing/ch-samplestores.md#contexthub-surferinfo-sample-store-candidate) opslagkandidaat wordt gebaseerd.

![chlimage_1-77](assets/chlimage_1-77a.png)

De broncode voor de module UI bevindt zich in /libs/granite/contexthub/components/modules/browserinfo. Hoewel contextthub.browserinfo de contexthub.base UI-module uitbreidt, overschrijft of biedt deze geen extra functies. De implementatie biedt een standaardconfiguratie voor het renderen van browserinformatie.

### Configuratie {#configuration-1}

Instanties van de module Contextthub.browserinfo UI vereisen geen waarde voor de Configuratie van het Detail. De volgende JSON-tekst vertegenwoordigt de standaardconfiguratie van de module.

```xml
{
   "icon":"coral-Icon--globe",
   "title":"Browser/OS Information",
   "storeMapping":{"surferinfo":"surferinfo"},
   "template":"<p>{{surferinfo.browser.family}} {{surferinfo.browser.version}}</p><p>{{surferinfo.os.name}} {{surferinfo.os.version}}</p>"
}
```

## contexthub.datetime UI-moduletype {#contexthub-datetime-ui-module-type}

De contexthub.datetime UI module toont de datum en de tijd die in een opslag genoemd datetime wordt opgeslagen die op [contexthub.datetime](/help/sites-developing/ch-samplestores.md#contexthub-datetime-sample-store-candidate) opslagkandidaat gebaseerd is.

![chlimage_1-78](assets/chlimage_1-78a.png)

De module verstrekt een popover vorm die u toelaat om de datum en de tijd in de opslag te veranderen.

De bron van de contexthub.datetime UI-module bevindt zich in /libs/granite/contexthub/components/modules/datetime.

### Configuratie {#configuration-2}

Instanties van de module Contextthub.datetime UI vereisen geen waarde voor de Configuratie van het Detail. De volgende JSON-tekst vertegenwoordigt de standaardconfiguratie van de module.

```xml
{
   "icon":"coral-Icon--clock",
   "title":"DATE&TIME",
   "clickable":true,
   "storeMapping":{"d":"datetime"},
   "template":"<p class=\"contexthub-module-line1\">{{i18n \"Date&Time\"}}</p><p class=\"contexthub-module-line2\">{{d.formatted.locale.date}} {{d.formatted.locale.time}}</p>",
   "popoverTemplate":"<div class=\"datetime center\"><div class=\"coral-DatePicker-calendar\" data-init=\"datepicker\"><input class=\"coral-Textfield\" type=\"datetime\" value=\"{{d.formatted.iso}}\"><button class=\"coral-Button coral-Button--secondary coral-Button--square\" title=\"{{i18n \"Datetime picker\"}}\"><i class=\"coral-Icon coral-Icon--calendar coral-Icon--sizeS\"></i></button></div></div>"
}
```

## contexthub.location UI Module Type {#contexthub-location-ui-module-type}

In de module contexthub.location UI worden de lengte en breedte van de client weergegeven. De module biedt een pop-up die een Google-kaart weergeeft waarop u kunt klikken om de huidige locatie te wijzigen. De module verkrijgt informatie van een opslag ContextHub genoemd geolocation die op [contexthub.geolocation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) opslagkandidaat gebaseerd is.

![chlimage_1-80](assets/chlimage_1-80a.png)

De bron van de UI-module bevindt zich op /etc/cloudsettings/default/contexthub/geolocation.

### Configuratie {#configuration-4}

Instanties van de module contexthub.location UI vereisen geen waarde voor de Configuratie van het Detail. De volgende JSON-tekst vertegenwoordigt de standaardconfiguratie van de module.

```xml
{
 "icon":"coral-Icon--compass",
 "title":"Location",
 "clickable":true,
 "editable":{"key":"/geolocation","disabled":[],"hidden":["/geolocation/generatedThumbnail","/geolocation/city","/geolocation/country"]},
 "fullscreen":true,
 "storeMapping":{"g":"geolocation"},
 "template":"<p>{{i18n \"Location\"}}</p><p>{{g.address.postalCode}} {{g.address.city}}{{#if g.address.city}}{{#if g.address.region}},{{/if}}{{/if}} {{g.address.region}}</p>",
 "list":[
  {"title":"Basel, Switzerland",
  "data":{"longitude":7.58929,"latitude":47.554746,"city":"Basel","country":"Switzerland"}},
  {"title":"Melbourne, Australia",
  "data":{"longitude":144.96328,"latitude":-37.814107,"city":"Melbourne","country":"Australia"}},
  {"title":"Beijing, China",
  "data":{"longitude":116.407526,"latitude":39.90403,"city":"Beijing","country":"China"}},
  {"title":"New York, NY, USA",
  "data":{"longitude":-74.005973,"latitude":40.714353,"city":"New York","country":"United States"}},
  {"title":"Paris, France",
  "data":{"longitude":2.352222,"latitude":48.856614,"city":"Paris","country":"France"}},
  {"title":"Rio de Janeiro, Brazil",
  "data":{"longitude":-43.20071,"latitude":-22.913395,"city":"Rio","country":"Brazil"}},
  {"title":"San Jose, CA, USA",
  "data":{"longitude":-121.894955,"latitude":37.339386,"city":"San Jose","country":"United States"}},
  {"title":"Tokyo, Japan",
  "data":{"longitude":139.691706,"latitude":35.689487,"city":"Shinjuku","country":"Japan"}}
 ],
 "listType":"checkmark"
}
```

## contexthub.screen-orientation UI Module Type {#contexthub-screen-orientation-ui-module-type}

In de UI-module contextthub.screen-orientation wordt de huidige schermoriëntatie van de client weergegeven. Hoewel standaard uitgeschakeld, biedt de module een pop-up waarmee u een richting kunt selecteren. De module verkrijgt informatie van een opslag ContextHub genoemd mededingers die op [granite.emulators](/help/sites-developing/ch-samplestores.md#granite-emulators-sample-store-candidate) opslagkandidaat gebaseerd is.

![chlimage_1-81](assets/chlimage_1-81a.png)

De bron van de module UI bevindt zich bij /libs/granite/contexthub/components/modules/screen-orientation.

### Configuratie {#configuration-5}

Instanties van de contexthub.screen-orientation UI module vereisen geen waarde voor de Configuratie van het Detail. De volgende JSON-tekst vertegenwoordigt de standaardconfiguratie van de module. De eigenschap `clickable` is standaard `false`. Als u de standaardconfiguratie aan reeks `clickable` aan `true` met voeten treedt, openbaart het klikken van de module popup waar u de richtlijn kunt selecteren.

```xml
{
   "icon":"coral-Icon--rotateRight",
   "title":"Screen Orientation",
   "clickable":false,
   "storeMapping":{"emulator":"emulators"},
   "template":"<p>{{{ i18n \"Screen Orientation\" }}}</p><p>{{{ emulator.currentDevice.orientation }}}",
   "listReference":"/emulators/orientations",
   "listType":"checkmark"
}
```

## contexthub.tagcloud UI Module Type {#contexthub-tagcloud-ui-module-type}

In de module Contextthub.tagcloud UI wordt informatie over tags weergegeven. In de werkbalk wordt in de gebruikersinterface het aantal codes weergegeven. De pop-up onthult een geëtiketteerde wolk en een texbox voor het toevoegen van nieuwe markeringen. De module UI verkrijgt informatie van een opslag ContextHub genoemd tagcloud die op [contexthub.tagcloud](/help/sites-developing/ch-samplestores.md#contexthub-tagcloud-sample-data-store) opslagkandidaat gebaseerd is.

![chlimage_1-82](assets/chlimage_1-82a.png)

De bron van de UI-module bevindt zich op /libs/granite/contexthub/components/modules/tagcloud.

### Configuratie {#configuration-6}

Voor instanties van de module Contextthub.tagcloud UI is geen waarde vereist voor de detailconfiguratie. De volgende JSON-tekst vertegenwoordigt de standaardconfiguratie van de module.

```xml
{
   "icon":"coral-Icon--tag",
   "title":"TagCloud",
   "clickable":true,
   "storeMapping":{"t":"tagcloud"},
   "maxTags":20,
   "template":"<p class=\"contexthub-module-line1\">{{i18n \"TagCloud\"}}</p><p class=\"contexthub-module-line2\">{{stats.total}} {{i18n \"Tags\"}}</p>",
   "popoverTemplate":"<div class=\"contexthub-popover-content center\"><p class=\"stats\">{{stats.total}} {{i18n \"Tags\"}} | {{stats.hits}} {{i18n \"Hits\"}} | {{i18n \"Last tag\"}}: {{#if stats.recent}}{{stats.recent}}{{else}}{{i18n \"Unknown\"}}{{/if}}</p><p class=\"tagcloud\">{{#each tags}}<span class=\"tag{{this.weight}}\">{{this.name}}</span> {{/each}}</p><div class=\"coral-InputGroup\"><input type=\"text\" class=\"coral-InputGroup-input coral-Textfield tag-name\" placeholder=\"{{i18n \"Add a namespace:my/tag\"}}\" pattern=\"^[A-Za-z0-9_\\-]+(:[A-Za-z0-9_\\-\\/]+)?$\" title=\"{{i18n \"namespace:my/tag\"}}\"><span class=\"coral-InputGroup-button\"><button class=\"coral-Button coral-Button--secondary coral-Button--square contexthub-new-tag\" type=\"button\" title=\"{{i18n \"increment\"}}\"><i class=\"coral-Icon coral-Icon--sizeS coral-Icon--add\"></i></button></span></div></div>"
}
```

## granite.profile UI-moduletype {#granite-profile-ui-module-type}

De granite.profile module ContextHub UI toont de vertoningsnaam van de huidige gebruiker. De pop-up openbaart de login naam van de gebruiker en laat u toe om de waarde van de vertoningsnaam te veranderen. De module UI verkrijgt informatie van een opslag ContextHub genoemd profiel dat op [granite.profile](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) opslagkandidaat gebaseerd is.

![chlimage_1-83](assets/chlimage_1-83a.png)

De bron van de module UI is in /libs/granite/contexthub/components/modules/profile.

### Configuratie {#configuration-7}

De instanties van de module grantie.profile UI vereisen geen waarde voor de Configuratie van het Detail. De volgende JSON-tekst vertegenwoordigt de standaardconfiguratie van de module.

```xml
{
   "icon":"coral-Icon--user",
   "title":"Profile",
   "clickable":true,
   "editable":{
      "key":"/profile",
      "disabled":["/profile/authorizableId"],
      "hidden":["/profile/avatar","/profile/path"]},
   "storeMapping":{"p":"profile"},
   "template":"<p class=\"contexthub-module-line1\">{{i18n \"Persona\"}}</p><p class=\"contexthub-module-line2\">{{p.displayName}}</p>",
   "listType":"checkmark"
}
```
