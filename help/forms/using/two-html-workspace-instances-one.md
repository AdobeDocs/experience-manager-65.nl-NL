---
title: Twee AEM Forms-werkruimteinstanties op één server hosten
description: Hoe LC-beheerders HTML WS kunnen aanpassen om twee instanties op één server te hosten die via verschillende URL's toegankelijk zijn.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 32a546fc-e33f-46f9-ac3b-45eca0e12239
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 1%

---

# Twee AEM Forms-werkruimteinstanties op één server hosten {#hosting-two-aem-forms-workspace-instances-on-one-server}

Bij de standaardinstallatie en -instellingen van AEM Forms kan slechts één AEM Forms-werkruimte beschikbaar zijn op de server. Het is echter mogelijk dat u twee verschillende versies van de AEM Forms-werkruimte op één AEM Forms-server moet hosten. De twee instanties zijn toegankelijk door verschillende URL&#39;s.

AEM Forms-beheerders passen de werkruimte aan om twee verschillende URL&#39;s te maken en twee werkruimten beschikbaar te maken op dezelfde server. In dit aanpassingsartikel kunt u ervan uitgaan dat de twee werkruimten toegankelijk zijn via `https://'[server]:[port]'/lc/ws` en `https://'[server]:[port]':/lc/ws2` .

Voer de volgende stappen uit om de AEM Forms-werkruimte te configureren.

1. Installeer het ontwikkelingspakket van de AEM Forms-werkruimte op uw server. Zie [&#x200B; dev pakket &#x200B;](/help/forms/using/introduction-customizing-html-workspace.md#p-crx-package-p), voor instructies om het tot stand te brengen.
1. Meld u als beheerder aan bij CRXDE Lite door `https://'[server]:[port]'/lc/crx/de/index.jsp` te openen.
1. De knooprijen van het exemplaar bij /content en deeg bij /content. Naam knooppunt wijzigen in ws2. Klik op **[!UICONTROL Save all]**. Wijzig in eigenschappen van dit knooppunt de waarde `sling:resourceType` in ws2. Klik op **[!UICONTROL Save all]**.

1. Kopieer de mappenvensters van /libs en plak deze op /apps. Wijzig de naam van de map in ws2. Klik op **[!UICONTROL Save all]**.
1. Breng in `GET.jsp` at `/apps/ws2` de volgende codewijzigingen aan. Vervang het volgende

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

1. Wijzig in `registry.js` om `/apps/ws2/js` het pad van sjablonen om te verwijzen naar sjablonen op `/apps/ws2/js/runtime/templates` . De volgende code vervangen

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

1. Wijzig in `userinfo.js` at `/apps/ws2/js/runtime/models` en `/apps/ws2/js/runtime/views` de tekenreeks `/lc/content/ws` in `lc/content/ws2` .

1. Wijzig in `/apps/ws2/js/runtime/services/service.js` het pad in de functie `getLocalizationData` in punt naar `/lc/apps/ws2/Locale.html` .

1. Als u wilt verwijzen naar `pdf.html` van de nieuwe Workspace, wijzigt u het pad van `pdf.html` in `/apps/ws2/js/runtime/views/forms/pdftaskform.js` .

1. Als u naar `pdf.html` van de nieuwe Workspace wilt verwijzen, wijzigt u de paden `pdf.html` en `WsNextAdapter.swf` in `startprocess.html` , `taskdetails.html` en `processinstancehistory.html` at `/apps/ws2/js/runtime/templates` .

1. Kopieer de map `/etc/map/ws` en plak deze in `/etc/map` . Wijzig de naam van de nieuwe map in ws2. Klik op Alles opslaan.

1. Wijzig in eigenschappen van `ws2` de waarde `sling:redirect` to `content/ws2` .

1. Wijzig de waarde van `sling:match` in `^[^/\||]/[^/\||]/ws2$` .
