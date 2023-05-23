---
title: Het lettertype in de interface wijzigen
seo-title: Changing the font on the interface
description: Hoe u de lettertypen in de gebruikersinterface selectief kunt wijzigen.
seo-description: How to change the fonts on the user interface selectively.
uuid: 421fdd24-441a-4092-8c52-f3ed3d5d5671
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 9fcb80b4-cbc2-48a5-afd1-4f3bc50bc503
docset: aem65
exl-id: 226f70f0-8eb4-4724-b496-5801dc6b436f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---

# Het lettertype in de interface wijzigen{#changing-the-font-on-the-interface}

U kunt het lettertype wijzigen dat in de AEM Forms-werkruimte wordt weergegeven. Lettertypen die in een specifieke sectie van de gebruikersinterface worden gebruikt, worden gedefinieerd in de bijbehorende sectie van het stijlblad. U kunt de lettertypen in de gebruikersinterface selectief wijzigen.

Volg de [Algemene stappen voor aanpassing van de AEM Forms-werkruimte](../../forms/using/generic-steps-html-workspace-customization.md) en voert u, afhankelijk van uw vereisten, de stappen uit voor het aanpassen van CSS, HTML of beide.

1. Wijzig of voeg de lettertypefamilie toe aan een bestaande stijl.
1. Wijzig of voeg de lettertypefamilie inline voor het HTML-element toe.
1. Voeg een stijl toe en gebruik deze voor het HTML-element.

Voer bijvoorbeeld de volgende stappen uit als u het font van het ankerpunt op de bovenste navigatiebalk wilt wijzigen in Courier New:

1. Aanmelden bij CRXDE Lite via toegang `https://'[server]:[port]'/lc/crx/de/index.jsp`.
1. Voer een van de volgende handelingen uit:

   1. Als u de lettertypefamilie wilt wijzigen in een bestaande stijl, voegt u het volgende toe in het bestand newStyle.css op /apps/ws/css.

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. Als u de lettertypefamilie inline voor het HTML-element wilt toevoegen, kopieert u de `/libs/ws/js/runtime/templates/appnavigation.html` bestand naar `/apps/ws/js/runtime/templates/appnavigation.html`.

      Werk het bestand /apps/ws/js/runtime/templates/appnavigation.html als volgt bij:

      ```jsp
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      Het bestand /apps/ws/js/registry.js openen om te bewerken en te vervangen `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` with `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`.

   1. Als u een stijl wilt toevoegen die de lettertypefamilie definieert, voegt u het volgende toe in het bestand newStyle.css op /apps/ws/css.

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      Als u inline font-family voor het HTML-element wilt toevoegen, voegt u het volgende toe in het bestand appnavigation.html op /apps/ws/js/runtime/templates.

      ```jsp
      <div id="topnav" class="myNewFontStyle">
          <ul>
              <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
              <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>"><%= $.t('index.header.topnav.todo.name')%></a></li>
              <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
              <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
          </ul>
      </div>
      ```

1. Start de werkruimte opnieuw en wis de browsercache zodat de wijzigingen zichtbaar zijn.

![change_font_before](assets/change_font_before.png)

Bovenste navigatiebalk voor aanpassing van lettertypen

![change_font_after](assets/change_font_after.png)

Bovenste navigatiebalk na aanpassing van lettertype van eerste tab
