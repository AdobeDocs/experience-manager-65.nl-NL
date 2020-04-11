---
title: Twee AEM Forms-werkruimteinstanties hosten op één server
seo-title: Twee AEM Forms-werkruimteinstanties hosten op één server
description: Hoe LC-beheerders HTML WS kunnen aanpassen om twee instanties op één server te hosten die via verschillende URL's toegankelijk zijn.
seo-description: Hoe LC-beheerders HTML WS kunnen aanpassen om twee instanties op één server te hosten die via verschillende URL's toegankelijk zijn.
uuid: 0584f512-6b92-4418-b71c-93605cfa1927
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 1254a7c2-2c67-4661-803e-afd53e817916
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Twee AEM Forms-werkruimteinstanties hosten op één server {#hosting-two-aem-forms-workspace-instances-on-one-server}

Met de standaardinstallatie en -instellingen van AEM Forms kan slechts één werkruimte van AEM Forms beschikbaar zijn op de server. Het is echter mogelijk dat u twee verschillende exemplaren van de werkruimte van AEM Forms op één AEM Forms-server moet hosten. De twee instanties zijn toegankelijk door verschillende URL&#39;s.

AEM Forms beheerders passen de werkruimte aan om twee verschillende URL&#39;s te maken en twee werkruimten beschikbaar te maken op dezelfde server. In dit aanpassingsartikel gaan we ervan uit dat de twee werkruimten toegankelijk zijn bij `https://'[server]:[port]'/lc/ws` en `https://'[server]:[port]':/lc/ws2`.

Voer de volgende stappen uit om de werkruimte van AEM-formulieren te configureren.

1. Installeer het ontwikkelpakket van de werkruimte van Vormen AEM op uw server. Zie [Dev-pakket](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p)voor instructies om het te maken.
1. Meld u aan bij CRXDE Lite als beheerder door toegang te krijgen tot `https://'[server]:[port]'/lc/crx/de/index.jsp`.
1. De knooprijen van het exemplaar bij /content en deeg bij /content. Naam knooppunt wijzigen in ws2. Klik op Alles **** opslaan. In eigenschappen van dit knooppunt wijzigt u de waarde van `sling:resourceType` in ws2. Klik op Alles **** opslaan.

1. Kopieer de mappenvensters van /libs en plak deze op /apps. Wijzig de naam van de map in ws2. Klik op Alles **** opslaan.
1. Breng in `GET.jsp` bij `/apps/ws2`de volgende codewijzigingen aan. Vervang het volgende

   ```
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

   ```
   <html lang="en">
   <head>
       <meta charset="utf-8">
       <title>Workspace Next</title>
       <meta http-equiv="refresh" content="0;URL='/lc/apps/ws2/index.html'" />
   ```

1. Wijzig in `registry.js` om `/apps/ws2/js`het pad van sjablonen om naar sjablonen te verwijzen bij `/apps/ws2/js/runtime/templates`. De volgende code vervangen

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

1. In `userinfo.js` bij `/apps/ws2/js/runtime/models` en `/apps/ws2/js/runtime/views`, verander koord `/lc/content/ws` in `lc/content/ws2`.

1. Wijzig `/apps/ws2/js/runtime/services/service.js`in functie het pad in `getLocalizationData` richting `/lc/apps/ws2/Locale.html`.

1. Als u wilt verwijzen naar `pdf.html` de nieuwe werkruimte, wijzigt u het pad van `pdf.html` in `/apps/ws2/js/runtime/views/forms/pdftaskform.js`.

1. Als u wilt verwijzen naar `pdf.html` de nieuwe werkruimte, wijzigt u paden van `pdf.html` en `WsNextAdapter.swf` in, `startprocess.html`en `taskdetails.html`bij `processinstancehistory.html` `/apps/ws2/js/runtime/templates`.

1. Kopieer de `/etc/map/ws` map en plak deze in `/etc/map`. Wijzig de naam van de nieuwe map in ws2. Klik op Alles opslaan.

1. Wijzig in eigenschappen van `ws2`, waarde van `sling:redirect` in `content/ws2`.

1. Waarde wijzigen van `sling:match` in `^[^/\||]/[^/\||]/ws2$`.
