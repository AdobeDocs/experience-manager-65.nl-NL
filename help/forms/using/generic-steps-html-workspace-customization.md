---
title: Algemene stappen voor aanpassing van de AEM Forms-werkruimte
seo-title: Algemene stappen voor aanpassing van de AEM Forms-werkruimte
description: Aan de slag met het aanpassen van de gebruikersinterface van de AEM Forms-werkruimte.
seo-description: Aan de slag met het aanpassen van de gebruikersinterface van de AEM Forms-werkruimte.
uuid: da6310b4-1c58-468d-85c6-975fd2c141f9
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: dd3218c4-2bb2-40fc-9141-5823b0ea4224
docset: aem65
translation-type: tm+mt
source-git-commit: 998a127ce00c6cbb3db3a81d8a89d97ab9ef7469
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 3%

---


# Algemene stappen voor aanpassing van de AEM Forms-werkruimte{#generic-steps-for-aem-forms-workspace-customization}

De algemene stappen voor het uitvoeren van aanpassingen zijn:

1. Meld u aan bij CRXDE Lite door `https://'[server]:[port]'/lc/crx/de/index.jsp` te openen.
1. Maak een map met de naam `ws`op `/apps` als deze niet bestaat. Klik op **[!UICONTROL Save All]**.
1. Blader naar `/apps/ws` en navigeer naar het tabblad **[!UICONTROL Access Control]**.
1. Klik in de lijst **[!UICONTROL Access Control]** op **[!UICONTROL +]** om een nieuwe vermelding toe te voegen. Klik nogmaals **[!UICONTROL +]**.
1. Zoek en selecteer **PERM_WORKSPACE_USER** Principal.

   ![Selecteer PERM_WORKSPACE_USER principal als onderdeel van de algemene stappen om de HTML-werkruimte aan te passen](assets/perm_workspace_user.png)

1. Geef `jcr:read` voorrecht aan Opdrachtgever.
1. Klik op **[!UICONTROL Save All]**.
1. Kopieer de `GET.jsp`- en `html.jsp`-bestanden van de map `/libs/ws`naar de map `/apps/ws`.
1. Kopieer de map `/libs/ws/locales` in de map `/apps/ws`. Klik op **[!UICONTROL Save All]**.
1. Werk de verwijzingen en relatieve wegen in het `GET.jsp` dossier bij, zoals hieronder getoond, en klik **[!UICONTROL Save all]**.

   ```javascript
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Ga als volgt te werk voor CSS-aanpassingen:

   1. Navigeer naar de map `/apps/ws` en maak een nieuwe map met de naam `css`.

   1. Maak in de map `css`een nieuw bestand met de naam `newStyle.css`.

   1. `/apps/ws/html`.jsp openen en wijzigen van

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
   >Plaats de vermelding van het door de gebruiker gedefinieerde CSS-bestand na de vermelding newStyle.css, zoals hierboven weergegeven.

1. Wijzig in het bestand /apps/ws/html.jsp

   ```jsp
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   tot

   ```jsp
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Ga als volgt te werk:

   1. Maak een map met de naam `js`op `/apps/ws`. Klik op **[!UICONTROL Save All]**.

   1. Maak een map met de naam `libs`op `/apps/ws/js`. Klik op **[!UICONTROL Save All]**.

   1. Maak een map met de naam `jqueryui`op `/apps/ws/js/libs`. Klik op **[!UICONTROL Save All]**.

   1. Kopieer `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` naar `/apps/ws/js/libs/jqueryui`. Klik op **[!UICONTROL Save All]**.

1. Ga als volgt te werk voor HTML-aanpassingen:

   1. Maak onder `/apps/ws/js` een map met de naam `runtime`. Klik op **[!UICONTROL Save All]**.

   1. Maak onder `/apps/ws/js/runtime` een map met de naam `templates`. Klik op **[!UICONTROL Save All]**.

   1. Kopieer `/libs/ws/js/main.js` naar `/apps/ws/js/main.js`.

   1. Kopieer /libs/ws/js/registry.js naar `/apps/ws/js/registry.js`.

1. Klik **[!UICONTROL Save All]**, ontruim geheime voorgeheugen, en vernieuw de werkruimte van AEM Forms.

   Open de URL `https://'[server]:[port]'/lc/ws` en meld u aan met de gegevens voor de beheerder/het wachtwoord. De browser wordt omgeleid naar `https://'[server]:[port]'/lc/apps/ws/index.html`.
