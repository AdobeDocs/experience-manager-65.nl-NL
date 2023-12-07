---
title: Het bedrijfslogo voor branding wijzigen
description: Als u een merk wilt aanbrengen in de AEM Forms-werkruimte, kunt u het logo van uw organisatie opgeven door het standaardlogo aan te passen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 49572f2a-f3ec-4ee6-98b8-2563de1cf96c
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Het bedrijfslogo voor branding wijzigen {#changing-the-organization-logo-for-branding}

Het bedrijfslogo wordt linksboven in de AEM Forms-werkruimte weergegeven. Als u het logo wilt bijwerken, volgt u de [Algemene stappen voor aanpassing van de AEM Forms-werkruimte](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) en dan de volgende stappen.

1. Een logo maken en het bestand een naam geven `NewWorkspace.png`. Plaats het afbeeldingsbestand in de map /apps/ws/images met een WebDAV-client.

   >[!NOTE]
   >
   >De aanbevolen grootte van de logoafbeelding is 218 px × 20 px.

   >[!NOTE]
   >
   >Voor meer informatie over WebDAV toegang, zie [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=en).

1. Verwijs naar de nieuwe logoafbeelding in stijlblad op /apps/ws/css/newStyle.css door volgende stijl toe te voegen.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;
   
   }
   ```
