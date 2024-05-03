---
title: Twee AEM Forms-werkruimteinstanties op één server hosten
description: Hoe LC-beheerders HTML WS kunnen aanpassen om twee instanties op één server te hosten die via verschillende URL's toegankelijk zijn.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 32a546fc-e33f-46f9-ac3b-45eca0e12239
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 1%

---

# Twee AEM Forms-werkruimteinstanties op één server hosten {#hosting-two-aem-forms-workspace-instances-on-one-server}

Bij de standaardinstallatie en -instellingen van AEM Forms kan slechts één AEM Forms-werkruimte beschikbaar zijn op de server. Het is echter mogelijk dat u twee verschillende versies van de AEM Forms-werkruimte op één AEM Forms-server moet hosten. De twee instanties zijn toegankelijk door verschillende URL&#39;s.

AEM Forms-beheerders passen de werkruimte aan om twee verschillende URL&#39;s te maken en twee werkruimten beschikbaar te maken op dezelfde server. In dit aanpassingsartikel, kunt u veronderstellen dat de twee werkruimten bij toegankelijk zijn `https://'[server]:[port]'/lc/ws` en `https://'[server]:[port]':/lc/ws2`.

Voer de volgende stappen uit om de AEM Forms-werkruimte te configureren.

1. Installeer het ontwikkelingspakket van de AEM Forms-werkruimte op uw server. Zie [dev-pakket](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p), voor instructies om het te creëren.
1. Meld u als beheerder aan bij CRXDE Lite door toegang te krijgen tot `https://'[server]:[port]'/lc/crx/de/index.jsp`.
1. De knooprijen van het exemplaar bij /content en deeg bij /content. Naam knooppunt wijzigen in ws2. Klik op **[!UICONTROL Save all]**. In eigenschappen van dit knooppunt wijzigt u de waarde van `sling:resourceType` naar ws2. Klik op **[!UICONTROL Save all]**.

1. Kopieer de mappenvensters van /libs en plak deze op /apps. Wijzig de naam van de map in ws2. Klik op **[!UICONTROL Save all]**.
1. In `GET.jsp` om `/apps/ws2`, brengt u de volgende codewijzigingen aan. Vervang het volgende

   ```html
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" /><html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/libs/ws/index.html'" />
   ```

   met de volgende code

   ```html
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/apps/ws2/index.html'" />
   ```

1. In `registry.js` om `/apps/ws2/js`wijzigt u het pad van sjablonen om naar sjablonen te verwijzen op `/apps/ws2/js/runtime/templates`. De volgende code vervangen

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/libs/ws/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

   met de volgende code

   ```css
   "tasklist" : {
   "name": "tasklist",
   "path": "tasklistview",
   "model": "tasklist",
   "template": "text!/lc/apps/ws2/js/runtime/templates/tasklist.html",
   "utility": "utility",
   "view": "taskview",
   "errorModel": null
   }
   ```

1. In `userinfo.js` om `/apps/ws2/js/runtime/models` en `/apps/ws2/js/runtime/views`, tekenreeks wijzigen `/lc/content/ws` tot `lc/content/ws2`.

1. In `/apps/ws2/js/runtime/services/service.js`wijzigt u het pad in `getLocalizationData` functie om naar `/lc/apps/ws2/Locale.html`.

1. Zie `pdf.html` van de nieuwe werkruimte wijzigt u het pad van `pdf.html` in `/apps/ws2/js/runtime/views/forms/pdftaskform.js`.

1. Zie `pdf.html` van de nieuwe werkruimte, wijzigt u paden van `pdf.html` en `WsNextAdapter.swf` in `startprocess.html`, `taskdetails.html`, en `processinstancehistory.html` om `/apps/ws2/js/runtime/templates`.

1. Kopiëren `/etc/map/ws` map en plakken op `/etc/map`. Wijzig de naam van de nieuwe map in ws2. Klik op Alles opslaan.

1. In eigenschappen van `ws2`, waarde wijzigen van `sling:redirect` tot `content/ws2`.

1. Waarde wijzigen van `sling:match` tot `^[^/\||]/[^/\||]/ws2$`.
