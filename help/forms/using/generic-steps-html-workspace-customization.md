---
title: Algemene stappen voor aanpassing van de AEM Forms-werkruimte
description: Aan de slag met het aanpassen van de gebruikersinterface van de Adobe Experience Manager Forms-werkruimte.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 45e50b47-1b36-4937-9e1a-cc7bfb953861
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 2%

---

# Algemene stappen voor aanpassing van de AEM Forms-werkruimte {#generic-steps-for-aem-forms-workspace-customization}

De algemene stappen voor het uitvoeren van aanpassingen zijn:

1. Log in bij CRXDE Lite door toegang te krijgen `https://'[server]:[port]'/lc/crx/de/index.jsp`.
1. Een `sling:Folder` map met een naam `ws` om `/apps`, als deze niet bestaat. Een `sling:Folder` map, klikt u met de rechtermuisknop op de `apps` map en selecteer **[!UICONTROL Create]** > **[!UICONTROL Create Node]**. Geef de naam op als `ws`, selecteert u tekst als `sling:Folder`en klik op **[!UICONTROL OK]**. Klik op **[!UICONTROL Save All]**.
1. Bladeren naar `/apps/ws`en navigeer naar de **[!UICONTROL Access Control]** tab.
1. Selecteer de **[!UICONTROL Repository]** -optie. In de **[!UICONTROL Access Control]** lijst, klik **[!UICONTROL +]** om een item toe te voegen. Klikken **[!UICONTROL +]** opnieuw.
1. Zoek en selecteer de **PERM_WORKSPACE_USER** Opdrachtgever

   ![Selecteer PERM_WORKSPACE_USER principal als onderdeel van de algemene stappen om de HTML Workspace aan te passen](assets/perm_workspace_user.png)

1. Geef `jcr:read` aan de Opdrachtgever.
1. Klik op **[!UICONTROL Save All]**.
1. De `GET.jsp`, `index`, en `html.jsp` bestanden van de `/libs/ws` aan de `/apps/ws` map.
1. De `/libs/ws/locales` in de `/apps/ws` map. Klik op **[!UICONTROL Save All]**.
1. De verwijzingen en relatieve paden in het dialoogvenster `GET.jsp` bestand, zoals hieronder weergegeven, en klik op **[!UICONTROL Save all]**.

   ```javascript
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Ga als volgt te werk voor CSS-aanpassingen:

   1. Ga naar de `/apps/ws` en maak een map met de naam `css`.

   1. In de `css` map, maakt u een bestand met de naam `newStyle.css`.

   1. Openen `/apps/ws/html`.jsp en wijzigen van

   ```javascript
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   tot

   ```javascript
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >Plaats de vermelding van het door de gebruiker gedefinieerde CSS-bestand na de vermelding style.css, zoals hierboven weergegeven.

1. Wijzig in het bestand /apps/ws/html.jsp

   ```jsp
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   tot

   ```jsp
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Ga als volgt te werk:

   1. Een map maken met de naam `js` om `/apps/ws`. Klik op **[!UICONTROL Save All]**.

   1. Een map maken met de naam `libs` om `/apps/ws/js`. Klik op **[!UICONTROL Save All]**.

   1. Kopiëren `/libs/ws/js/libs/jqueryui` map naar `/apps/ws/js/libs`. Klik op **[!UICONTROL Save All]**.

1. Doe het volgende voor HTML aanpassingen:

   1. Onder `/apps/ws/js`, maakt u een map met de naam `runtime`. Klik op **[!UICONTROL Save All]**.

   1. Onder `/apps/ws/js/runtime`, maakt u een map met de naam `templates`. Klik op **[!UICONTROL Save All]**.

   1. Kopiëren `/libs/ws/js/main.js` tot `/apps/ws/js/main.js`.

   1. /libs/ws/js/registry.js kopiëren naar `/apps/ws/js/registry.js`.

1. Klikken **[!UICONTROL Save All]**, de cache wissen en de AEM Forms-werkruimte vernieuwen.

   De URL openen `https://'[server]:[port]'/lc/ws` en meld u aan met de gegevens van de beheerder/het wachtwoord. De browser wordt omgeleid naar `https://'[server]:[port]'/lc/apps/ws/index.html`.
