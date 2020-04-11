---
title: Het bedrijfslogo voor branding wijzigen
seo-title: Het bedrijfslogo voor branding wijzigen
description: Als u de werkruimte van AEM Forms van een merk wilt voorzien, verschaft u het logo van uw organisatie door het standaardlogo aan te passen.
seo-description: Als u de werkruimte van AEM Forms van een merk wilt voorzien, verschaft u het logo van uw organisatie door het standaardlogo aan te passen.
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Het bedrijfslogo voor branding wijzigen {#changing-the-organization-logo-for-branding}

Het bedrijfslogo wordt linksboven in de werkruimte van AEM Forms weergegeven. Als u het logo wilt bijwerken, voert u de [algemene stappen van de aanpassing](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) van de werkruimte van AEM Forms uit en voert u de volgende stappen uit.

1. Maak een logo en noem het bestand als `NewWorkspace.png`. Plaats het afbeeldingsbestand in de map /apps/ws/images met een WebDAV-client.

   >[!NOTE]
   >
   >De aanbevolen grootte van de logoafbeelding is 218 px × 20 px.

   >[!NOTE]
   >
   >Ga voor meer informatie over WebDAV-toegang naar [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. Verwijs naar de nieuwe logoafbeelding in stijlblad op /apps/ws/css/newStyle.css door volgende stijl toe te voegen.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;
   
   }
   ```
