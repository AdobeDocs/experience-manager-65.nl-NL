---
title: De koppeling naar de documentatie bijwerken
seo-title: De koppeling naar de documentatie bijwerken
description: Hoe kan ik de doelkoppeling van Workspace Help in de AEM Forms-werkruimte bijwerken zodat deze naar de koppeling voor aangepaste documentatie verwijst.
seo-description: Hoe kan ik de doelkoppeling van Workspace Help in de AEM Forms-werkruimte bijwerken zodat deze naar de koppeling voor aangepaste documentatie verwijst.
uuid: 64056d10-1451-44ed-8f25-81a21037dc75
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 788c427f-190f-4580-9efd-6a4c4a008837
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# De koppeling naar de documentatie {#updating-the-link-to-the-documentation} bijwerken

U kunt de standaardHelp-inhoud voor de AEM Forms-werkruimte openen door **Help > Werkruimte Help** te selecteren. Het verwijst naar de online documentatie op de website Adobe. U kunt de URL echter bijwerken zodat deze naar een andere URL verwijst.

Overweeg de volgende gebruiksgevallen waarin u de standaard Help-URL wilt wijzigen:

* Voor het bieden van gelokaliseerde hulp in een taal van uw keus.
* Voor het aanbieden van aangepaste Help-inhoud voor uw aangepaste werkruimte.

Als u de URL van de onlinedocumentatie wilt bijwerken, volgt u [Algemene stappen voor aanpassing](/help/forms/using/generic-steps-html-workspace-customization.md) en vervolgens de volgende stappen.

1. Kopieer het `userinfo.html`-bestand van `/libs/ws/js/runtime/templates` naar `/apps/ws/js/runtime/templates`.
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
   1. `text!/lc/libs/ws/js/runtime/templates/userinfo.html` doorzoeken en vervangen door `text!/lc/apps/ws/js/runtime/templates/userinfo.html`.
