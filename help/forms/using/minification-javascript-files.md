---
title: Miniatuur van de JavaScript-bestanden
seo-title: Minification of the JavaScript files
description: Instructies voor het genereren van geminificeerde code na aanpassingen in de AEM Forms-werkruimte om de JS-bestanden voor het web te optimaliseren.
seo-description: Instructions to generate minified code after AEM Forms workspace customizations to optimize the JS files for the web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
exl-id: d88c6831-8ae9-426d-acb5-2a7e066ad158
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 1%

---

# Miniatuur van de JavaScript-bestanden {#minification-of-the-javascript-files}

Met Minificatie worden de overbodige tekens, zoals witruimte, nieuwe regel en opmerkingen, uit de broncode verwijderd. Dit verbetert de prestaties door de grootte van de code te verminderen. De miniatuur heeft geen invloed op de functionaliteit, maar vermindert de leesbaarheid van de code.

Voer de volgende stappen uit om geminificeerde code voor semantische wijzigingen te genereren.

1. Kopiëren `client-html/src/main/webapp/js` van src-package op filesystem.

   >[!NOTE]
   >
   >Zie [Inleiding tot de AEM Forms-werkruimte aanpassen](/help/forms/using/introduction-customizing-html-workspace.md) voor meer informatie over de pakketten .

1. Paden bijwerken in `main.js` bevindt zich onder client-html/src/main/webapp/js, voor toegevoegde/bijgewerkte modellen/weergaven.

   Bijvoorbeeld, toevoeging van een nieuw model van de Schaduwrij, zeg mySharequeue, verandering:

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   ```

   Naar

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Bijwerken `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` in geval van wijziging/toevoeging van alias in `main.js`.

   Bijvoorbeeld, toevoeging van een nieuw model van de Schaduwrij, zeg mySharequeue, verandering:

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/models/sharequeue.js"
               service="service"/>
   ```

   Naar

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/myModels/mySharequeue.js"
               service="service"/>
   ```

1. Voer de opdracht uit op client-html/src/main/webapp/js/minifier:

   ```shell
   mvn clean install
   ```

   Er wordt een map met geminificeerde bestanden gegenereerd onder client-html/src/main/webapp/js met geminificeerde main.js en register.js.

>[!NOTE]
>
>Minificatie werkt alleen op 64-bits JVM.

>[!NOTE]
>
>Als u een minieme upgrade uitvoert, heeft dit gevolgen voor de upgrade.
