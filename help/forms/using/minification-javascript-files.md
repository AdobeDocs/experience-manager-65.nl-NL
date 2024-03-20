---
title: Miniatuur van de JavaScript-bestanden
description: Instructies voor het genereren van geminificeerde code na aanpassingen in de AEM Forms-werkruimte om de JS-bestanden voor het web te optimaliseren.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: d88c6831-8ae9-426d-acb5-2a7e066ad158
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Miniatuur van de JavaScript-bestanden {#minification-of-the-javascript-files}

Met Minificatie worden de overbodige tekens, zoals witruimte, nieuwe regels en opmerkingen, uit de broncode verwijderd. Dit verbetert de prestaties door de grootte van de code te verminderen. De miniatuur heeft geen invloed op de functionaliteit, maar vermindert de leesbaarheid van de code.

Voer de volgende stappen uit om geminificeerde code voor semantische wijzigingen te genereren.

1. Kopiëren `client-html/src/main/webapp/js` van src-package op filesystem.

   >[!NOTE]
   >
   >Zie [Inleiding tot de AEM Forms-werkruimte aanpassen](/help/forms/using/introduction-customizing-html-workspace.md) voor meer informatie over de pakketten .

1. Paden bijwerken in `main.js` bevindt zich onder client-html/src/main/webapp/js, voor toegevoegde/bijgewerkte modellen/weergaven.

   Bijvoorbeeld, de toevoeging van een nieuw model van de Schaduwrij, zeg mySharequeue, verandering:

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   ```

   Naar

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Bijwerken `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` in geval van wijziging/toevoeging van alias in `main.js`.

   Bijvoorbeeld, de toevoeging van een nieuw model van de Schaduwrij, zeg mySharequeue, verandering:

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

   Er wordt een map met geminificeerde bestanden gegenereerd, onder client-html/src/main/webapp/js met geminificeerde main.js en register.js.

>[!NOTE]
>
>Minificatie werkt alleen op een 64-bits JVM.

>[!NOTE]
>
>Als u een minieme upgrade uitvoert, heeft dit gevolgen voor de upgrade.
