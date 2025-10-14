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
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 2%

---

# Algemene stappen voor aanpassing van de AEM Forms-werkruimte {#generic-steps-for-aem-forms-workspace-customization}

De algemene stappen voor het uitvoeren van aanpassingen zijn:

1. Meld u aan bij CRXDE Lite door `https://'[server]:[port]'/lc/crx/de/index.jsp` te openen.
1. Maak een `sling:Folder` -map met de naam `ws` at `/apps` als deze niet bestaat. Als u een map `sling:Folder` wilt maken, klikt u met de rechtermuisknop op de map `apps` en selecteert u **[!UICONTROL Create]** > **[!UICONTROL Create Node]** . Geef de naam op als `ws` , selecteer tekst als `sling:Folder` en klik op **[!UICONTROL OK]** . Klik op **[!UICONTROL Save All]**.
1. Blader naar `/apps/ws` en navigeer naar het tabblad **[!UICONTROL Access Control]** .
1. Selecteer de optie **[!UICONTROL Repository]** . Klik in de lijst **[!UICONTROL Access Control]** op **[!UICONTROL +]** om een item toe te voegen. Klik nogmaals op **[!UICONTROL +]** .
1. Onderzoek en selecteer **PERM_WORKSPACE_USER** Belangrijk.

   ![&#x200B; Uitgezochte PERM_WORKSPACE_USER hoofd als deel van de generische stappen om HTML Workspace &#x200B;](assets/perm_workspace_user.png) aan te passen

1. Geef `jcr:read` bevoegdheid aan Opdrachtgever.
1. Klik op **[!UICONTROL Save All]**.
1. Kopieer de bestanden `GET.jsp` , `index` en `html.jsp` van de map `/libs/ws` naar de map `/apps/ws` .
1. Kopieer de map `/libs/ws/locales` in de map `/apps/ws` . Klik op **[!UICONTROL Save All]**.
1. Werk de referenties en relatieve paden in het `GET.jsp` -bestand bij, zoals hieronder wordt weergegeven, en klik op **[!UICONTROL Save all]** .

   ```javascript
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Ga als volgt te werk voor CSS-aanpassingen:

   1. Ga naar de map `/apps/ws` en maak een map met de naam `css` .

   1. Maak in de map `css` een bestand met de naam `newStyle.css` .

   1. `/apps/ws/html` .jsp openen en wijzigen vanuit

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

   1. Maak een map met de naam `js` op `/apps/ws` . Klik op **[!UICONTROL Save All]**.

   1. Maak een map met de naam `libs` op `/apps/ws/js` . Klik op **[!UICONTROL Save All]**.

   1. Kopieer `/libs/ws/js/libs/jqueryui` naar `/apps/ws/js/libs` . Klik op **[!UICONTROL Save All]**.

1. Doe het volgende voor HTML aanpassingen:

   1. Maak onder `/apps/ws/js` een map met de naam `runtime` . Klik op **[!UICONTROL Save All]**.

   1. Maak onder `/apps/ws/js/runtime` een map met de naam `templates` . Klik op **[!UICONTROL Save All]**.

   1. Kopieer `/libs/ws/js/main.js` naar `/apps/ws/js/main.js` .

   1. Kopieer /libs/ws/js/registry.js naar `/apps/ws/js/registry.js` .

1. Klik op **[!UICONTROL Save All]** , wis de cache en vernieuw de AEM Forms-werkruimte.

   Open de URL `https://'[server]:[port]'/lc/ws` en meld u aan met de beheerder-/wachtwoordreferenties. De browser wordt omgeleid naar `https://'[server]:[port]'/lc/apps/ws/index.html` .
