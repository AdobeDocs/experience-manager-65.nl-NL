---
title: Twee AEM Forms-werkruimteinstanties op één server hosten
seo-title: Twee AEM Forms-werkruimteinstanties op één server hosten
description: Hoe LC-beheerders HTML WS kunnen aanpassen om twee instanties op één server te hosten die via verschillende URL's toegankelijk zijn.
seo-description: Hoe LC-beheerders HTML WS kunnen aanpassen om twee instanties op één server te hosten die via verschillende URL's toegankelijk zijn.
uuid: 0584f512-6b92-4418-b71c-93605cfa1927
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 1254a7c2-2c67-4661-803e-afd53e817916
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Twee AEM Forms-werkruimteinstanties hosten op één server {#hosting-two-aem-forms-workspace-instances-on-one-server}

Bij de standaardinstallatie en -instellingen van AEM Forms kan slechts één AEM Forms-werkruimte beschikbaar zijn op de server. Het is echter mogelijk dat u twee verschillende exemplaren van de AEM Forms-werkruimte op één AEM Forms-server moet hosten. De twee instanties zijn toegankelijk door verschillende URL&#39;s.

AEM Forms-beheerders passen de werkruimte aan om twee verschillende URL&#39;s te maken en twee werkruimten beschikbaar te maken op dezelfde server. In dit aanpassingsartikel, veronderstellen wij de twee werkruimten toegankelijk bij `https://'[server]:[port]'/lc/ws` en `https://'[server]:[port]':/lc/ws2` zijn.

Voer de volgende stappen uit om de AEM Forms-werkruimte te configureren.

1. Installeer het ontwikkelingspakket van de AEM Forms-werkruimte op uw server. Zie [dev package](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p), voor instructies om het tot stand te brengen.
1. Meld u aan bij CRXDE Lite als beheerder door `https://'[server]:[port]'/lc/crx/de/index.jsp` te openen.
1. De knooprijen van het exemplaar bij /content en deeg bij /content. Naam knooppunt wijzigen in ws2. Klik op **[!UICONTROL Save all]**. Wijzig in eigenschappen van dit knooppunt de waarde `sling:resourceType` in ws2. Klik op **[!UICONTROL Save all]**.

1. Kopieer de mappenvensters van /libs en plak deze op /apps. Wijzig de naam van de map in ws2. Klik op **[!UICONTROL Save all]**.
1. Breng in `GET.jsp` om `/apps/ws2` de volgende codewijzigingen aan. Vervang het volgende

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

1. Wijzig in `registry.js` om `/apps/ws2/js` het pad van sjablonen om te verwijzen naar sjablonen op `/apps/ws2/js/runtime/templates`. De volgende code vervangen

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

1. Wijzig in `userinfo.js` om `/apps/ws2/js/runtime/models` en `/apps/ws2/js/runtime/views` de tekenreeks `/lc/content/ws` in `lc/content/ws2`.

1. Wijzig in `/apps/ws2/js/runtime/services/service.js` het pad in `getLocalizationData` functie om te wijzen naar `/lc/apps/ws2/Locale.html`.

1. Als u naar `pdf.html` van de nieuwe werkruimte wilt verwijzen, wijzigt u het pad van `pdf.html` in `/apps/ws2/js/runtime/views/forms/pdftaskform.js`.

1. Als u naar `pdf.html` van de nieuwe werkruimte wilt verwijzen, wijzigt u de paden van `pdf.html` en `WsNextAdapter.swf` in `startprocess.html`, `taskdetails.html` en `processinstancehistory.html` om `/apps/ws2/js/runtime/templates`.

1. Kopieer `/etc/map/ws` map en plak deze op `/etc/map`. Wijzig de naam van de nieuwe map in ws2. Klik op Alles opslaan.

1. Wijzig in eigenschappen van `ws2` de waarde `sling:redirect` in `content/ws2`.

1. Wijzig de waarde van `sling:match` in `^[^/\||]/[^/\||]/ws2$`.
