---
title: De koppeling naar de documentatie bijwerken
description: Hoe kan ik de koppeling naar Workspace Help in de AEM Forms-werkruimte bijwerken en naar de koppeling naar uw aangepaste documentatie verwijzen?
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: ca637bea-05c1-4920-9283-e782f07607de
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# De koppeling naar de documentatie bijwerken {#updating-the-link-to-the-documentation}

U kunt tot de standaardhulpinhoud voor de werkruimte van AEM Forms toegang hebben door **Hulp > Hulp van Workspace** te selecteren. Het verwijst naar de online documentatie op de website van Adobe. U kunt de URL echter bijwerken zodat deze naar een andere URL verwijst.

Overweeg de volgende gebruiksgevallen waarin u de standaard Help-URL wilt wijzigen:

* Voor het bieden van gelokaliseerde hulp in een taal van uw keus.
* Voor het aanbieden van aangepaste Help-inhoud voor uw aangepaste werkruimte.

Om URL van de online documentatie bij te werken, volg de [ Algemene Stappen van aanpassing ](/help/forms/using/generic-steps-html-workspace-customization.md) en toen de volgende stappen.

1. Kopieer het bestand `userinfo.html` van `/libs/ws/js/runtime/templates` naar `/apps/ws/js/runtime/templates` .
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
   1. Zoek en vervang `text!/lc/libs/ws/js/runtime/templates/userinfo.html` door `text!/lc/apps/ws/js/runtime/templates/userinfo.html` .
