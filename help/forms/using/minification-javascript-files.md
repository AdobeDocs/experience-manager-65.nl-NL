---
title: Miniatuur van de JavaScript-bestanden
seo-title: Miniatuur van de JavaScript-bestanden
description: Instructies voor het genereren van geminificeerde code na aanpassingen in de werkruimte van AEM Forms om de JS-bestanden voor het web te optimaliseren.
seo-description: Instructions to generate minified code after AEM Forms workspace customizations to optimize the JS files for the web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# Miniatuur van de JavaScript-bestanden {#minification-of-the-javascript-files}

Minification removes from the source code the redundant characters, such as white space, new line, and comments. Dit verbetert de prestaties door de grootte van de code te verminderen. While minification does not impact the functionality, it reduces the readability of the code.

Voer de volgende stappen uit om geminificeerde code voor semantische wijzigingen te genereren.

1. Kopieer `client-html/src/main/webapp/js` van het src-pakket naar het bestandssysteem.

   >[!NOTE]
   >
   >See [Introduction to Customizing AEM Forms workspace](/help/forms/using/introduction-customizing-html-workspace.md) for more details about the packages.

1. Werk paden bij `main.js` onder client-html/src/main/webapp/js voor toegevoegde/bijgewerkte modellen/weergaven.

   For example, addition of a new Sharequeue model, say mySharequeue, change:

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   ```

   Naar

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Update `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` in case there is change/addition of alias in `main.js`.

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

1. At client-html/src/main/webapp/js/minifier, run command:

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
