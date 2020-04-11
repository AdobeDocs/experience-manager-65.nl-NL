---
title: Algemene stappen voor aanpassing van de AEM-werkruimte
seo-title: Algemene stappen voor aanpassing van de AEM-werkruimte
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
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Algemene stappen voor aanpassing van de AEM-werkruimte{#generic-steps-for-aem-forms-workspace-customization}

De algemene stappen voor het uitvoeren van aanpassingen zijn:

1. Meld u aan bij CRXDE Lite door toegang te krijgen tot `https://'[server]:[port]'/lc/crx/de/index.jsp`.
1. Maak een map met de naam `ws`at `/apps`, als deze niet bestaat. Klik op Alles **[!UICONTROL opslaan]**.
1. Blader naar `/apps/ws`en navigeer naar het tabblad **[!UICONTROL Toegangsbeheer]** .
1. Klik in de lijst **[!UICONTROL Toegangsbeheer]** op **[!UICONTROL +]** om een nieuw item toe te voegen. Klik nogmaals **[!UICONTROL +]** .
1. Zoek en selecteer **PERM_WORKSPACE_USER** Principal.

   ![Selecteer PERM_WORKSPACE_USER principal als onderdeel van de algemene stappen om de HTML-werkruimte aan te passen](assets/perm_workspace_user.png)

1. Geef `jcr:read` recht aan Opdrachtgever.
1. Klik op Alles **[!UICONTROL opslaan]**.
1. Kopieer de `GET.jsp` bestanden en `html.jsp`bestanden vanuit de `/libs/ws`map naar de `/apps/ws` map.
1. Kopieer de `/libs/ws/locales` map in de `/apps/ws` map. Klik op Alles **[!UICONTROL opslaan]**.
1. Werk de verwijzingen en relatieve wegen in het `GET.jsp` dossier bij, zoals hieronder getoond, en klik **[!UICONTROL sparen allen]**.

   ```
   <meta http-equiv="refresh" content="0;URL='/lc/apps/ws/index.html'" />
   ```

1. Ga als volgt te werk voor CSS-aanpassingen:

   1. Navigeer naar de `/apps/ws` map en maak een nieuwe map met de naam `css`.

   1. Maak een nieuw bestand met de naam `css``newStyle.css`.

   1. Open `/apps/ws/html`.jsp en wijzig van

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/jquery-ui.css"/>
   ```

   tot

   ```css
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/style.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="css/newStyle.css" />
   <link lang="en" rel="stylesheet" type="text/css" href="../../libs/ws/css/jquery-ui.css"/>
   ```

   >[!NOTE]
   >
   >Plaats de vermelding van het door de gebruiker gedefinieerde CSS-bestand na de vermelding newStyle.css, zoals hierboven weergegeven.

1. Wijzig in het bestand /apps/ws/html.jsp

   ```css
   <script data-main="js/main" src="js/libs/require/require.js"></script>
   ```

   tot

   ```css
   <script data-main="js/main" src="../../libs/ws/js/libs/require/require.js"></script>
   ```

1. Ga als volgt te werk:

   1. Maak een map met de naam `js`at `/apps/ws`. Klik op Alles **[!UICONTROL opslaan]**.

   1. Maak een map met de naam `libs`at `/apps/ws/js`. Klik op Alles **[!UICONTROL opslaan]**.

   1. Maak een map met de naam `jqueryui`at `/apps/ws/js/libs`. Klik op Alles **[!UICONTROL opslaan]**.

   1. Kopiëren `/libs/ws/js/libs/jqueryui/jquery.ui.datepicker-ja.js` naar `/apps/ws/js/libs/jqueryui`. Klik op Alles **[!UICONTROL opslaan]**.

1. Ga als volgt te werk voor HTML-aanpassingen:

   1. Maak onder `/apps/ws/js`een map met de naam `runtime`. Klik op Alles **[!UICONTROL opslaan]**.

   1. Maak onder `/apps/ws/js/runtime`een map met de naam `templates`. Klik op Alles **[!UICONTROL opslaan]**.

   1. Kopiëren `/libs/ws/js/main.js` naar `/apps/ws/js/main.js`.

   1. Kopieer /libs/ws/js/registry.js naar `/apps/ws/js/registry.js`.

1. Klik op Alles **** opslaan, cache verwijderen en de werkruimte van AEM-formulieren vernieuwen.

   Open de URL `https://'[server]:[port]'/lc/ws` en meld u aan met de gegevens van de beheerder/het wachtwoord. De browser wordt omgeleid naar `https://'[server]:[port]'/lc/apps/ws/index.html`.
