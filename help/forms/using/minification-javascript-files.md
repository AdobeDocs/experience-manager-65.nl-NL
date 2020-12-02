---
title: Miniatuur van de JavaScript-bestanden
seo-title: Miniatuur van de JavaScript-bestanden
description: Instructies voor het genereren van geminificeerde code na aanpassingen in de AEM Forms-werkruimte om de JS-bestanden voor het web te optimaliseren.
seo-description: Instructies voor het genereren van geminificeerde code na aanpassingen in de AEM Forms-werkruimte om de JS-bestanden voor het web te optimaliseren.
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


# Minificatie van de JavaScript-bestanden {#minification-of-the-javascript-files}

Met Minificatie worden de overbodige tekens, zoals witruimte, nieuwe regel en opmerkingen, uit de broncode verwijderd. Dit verbetert de prestaties door de grootte van de code te verminderen. De miniatuur heeft geen invloed op de functionaliteit, maar vermindert de leesbaarheid van de code.

Voer de volgende stappen uit om geminificeerde code voor semantische wijzigingen te genereren.

1. Kopieer `client-html/src/main/webapp/js` van src-package op filesystem.

   >[!NOTE]
   >
   >Zie [Inleiding tot het aanpassen van de AEM Forms-werkruimte](/help/forms/using/introduction-customizing-html-workspace.md) voor meer informatie over de pakketten.

1. Werk paden bij in `main.js` onder client-html/src/main/webapp/js, voor toegevoegde/bijgewerkte modellen/weergaven.

   Bijvoorbeeld, toevoeging van een nieuw model van de Schaduwrij, zeg mySharequeue, verandering:

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   ```

   Naar

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` bijwerken voor het geval er een wijziging/toevoeging van alias in `main.js` is.

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
