---
title: Het bedrijfslogo voor branding wijzigen
description: Als u een merk wilt aanbrengen in de AEM Forms-werkruimte, kunt u het logo van uw organisatie opgeven door het standaardlogo aan te passen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: 49572f2a-f3ec-4ee6-98b8-2563de1cf96c
source-git-commit: 80e85ed78a26d784f4aa8e36c7de413cf9c03fa2
workflow-type: tm+mt
source-wordcount: '119'
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
   >Zie voor meer informatie [WebDAV-toegang](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/webdav-access.html?lang=en).

   [WebDAV-toegang](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/webdav-access.html?lang=en)

1. Verwijs naar de nieuwe logoafbeelding in stijlblad op /apps/ws/css/newStyle.css door volgende stijl toe te voegen.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;
   
   }
   ```
