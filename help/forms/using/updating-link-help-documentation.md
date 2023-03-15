---
title: De koppeling naar de documentatie bijwerken
seo-title: Updating the link to the documentation
description: Hoe kan ik de doelkoppeling van Workspace Help in de AEM Forms-werkruimte bijwerken zodat deze naar de koppeling voor aangepaste documentatie verwijst.
seo-description: How-to update the destination of Workspace Help link in AEM Forms workspace to point to your custom documentation link.
uuid: 64056d10-1451-44ed-8f25-81a21037dc75
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 788c427f-190f-4580-9efd-6a4c4a008837
exl-id: ca637bea-05c1-4920-9283-e782f07607de
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# De koppeling naar de documentatie bijwerken {#updating-the-link-to-the-documentation}

U kunt de standaard Help-inhoud voor de AEM Forms-werkruimte openen door **Help > Werkruimte Help**. Het verwijst naar de online documentatie op de website Adobe. U kunt de URL echter bijwerken zodat deze naar een andere URL verwijst.

Overweeg de volgende gebruiksgevallen waarin u de standaard Help-URL wilt wijzigen:

* Voor het bieden van gelokaliseerde hulp in een taal van uw keus.
* Voor het aanbieden van aangepaste Help-inhoud voor uw aangepaste werkruimte.

Als u de URL van de onlinedocumentatie wilt bijwerken, volgt u de [Algemene stappen voor aanpassing](/help/forms/using/generic-steps-html-workspace-customization.md) en dan de volgende stappen.

1. Kopieer de `userinfo.html` bestand van `/libs/ws/js/runtime/templates` tot `/apps/ws/js/runtime/templates`.
1. Wijzigen:

   ```html
   <ul class="helpmenu">
     <li>
       <a href="https://www.adobe.com/go/learn_aemforms_documentation_63" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

   tot

   ```html
   <ul class="helpmenu">
     <li>
       <a href="<!--place new help url here-->" title="<%= $.t('index.header.dropdown.WorkspaceHelp')%>" target="_blank"><%= $.t('index.header.dropdown.WorkspaceHelp')%></a>
     </li>
   ```

1. Ga als volgt te werk:

   1. Open /apps/ws/js/registry.js voor bewerking.
   1. Zoeken en vervangen `text!/lc/libs/ws/js/runtime/templates/userinfo.html` with `text!/lc/apps/ws/js/runtime/templates/userinfo.html`.
