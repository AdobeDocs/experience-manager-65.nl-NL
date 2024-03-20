---
title: De koppeling naar de documentatie bijwerken
description: Hoe kan ik de doelkoppeling van Workspace Help in de AEM Forms-werkruimte bijwerken zodat deze naar de koppeling voor aangepaste documentatie verwijst.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
exl-id: ca637bea-05c1-4920-9283-e782f07607de
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# De koppeling naar de documentatie bijwerken {#updating-the-link-to-the-documentation}

U kunt de standaard Help-inhoud voor de AEM Forms-werkruimte openen door **Help > Werkruimte Help**. Het verwijst naar de online documentatie op de website van Adobe. U kunt de URL echter bijwerken zodat deze naar een andere URL verwijst.

Overweeg de volgende gebruiksgevallen waarin u de standaard Help-URL wilt wijzigen:

* Voor het bieden van gelokaliseerde hulp in een taal van uw keus.
* Voor het aanbieden van aangepaste Help-inhoud voor uw aangepaste werkruimte.

Volg de [Algemene stappen voor aanpassing](/help/forms/using/generic-steps-html-workspace-customization.md) en dan de volgende stappen.

1. De `userinfo.html` bestand van `/libs/ws/js/runtime/templates` tot `/apps/ws/js/runtime/templates`.
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
