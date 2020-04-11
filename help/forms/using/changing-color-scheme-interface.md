---
title: Het kleurenschema van de interface wijzigen
seo-title: Het kleurenschema van de interface wijzigen
description: Het kleurenschema van de gebruikersinterfacegedeelten van de AEM Forms-werkruimte selectief aanpassen.
seo-description: Het kleurenschema van de gebruikersinterfacegedeelten van de AEM Forms-werkruimte selectief aanpassen.
uuid: 32c32f7a-8271-4d2c-8a1f-ad5ab3c90b83
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 18dab82a-badf-4c32-83a2-cd5cb04cae89
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Het kleurenschema van de interface wijzigen {#changing-the-color-scheme-of-the-interface}

U kunt het kleurschema van de gebruikersinterfacegedeelten van de AEM Forms-werkruimte aanpassen aan uw wensen. Hier volgen enkele voorbeelden van representatieve aanpassingen van kleurschema&#39;s. Naast de stappen die in dit artikel worden besproken, raadpleegt u [Algemene stappen voor aanpassing](/help/forms/using/generic-steps-html-workspace-customization.md)van de werkruimte van AEM Forms.

## Bovenste navigatiebalk {#top-navigation-bar}

### Achtergrondafbeelding gebruiken {#using-background-image}

De navigatiebalk boven in de werkruimte van AEM-formulieren bijwerken.

1. Maak een achtergrondafbeelding om de kleur bij te werken. Geef het bestand een naam als newBackground.jpg.
1. Upload het bestand met de achtergrondafbeelding in de map /apps/ws/images met een WebDAV-client.

   >[!NOTE]
   >
   >Ga voor meer informatie over WebDAV-toegang naar [https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html).

1. Verwijs naar de nieuwe achtergrondafbeelding in /apps/ws/css/newStyle.css door de volgende stijl toe te voegen.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### Kleureigenschap gebruiken in CSS {#using-color-property-in-css}

1. Voeg de volgende stijl toe aan newStyle.css op /apps/ws/css

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## Categorieonderdeel {#category-component}

De component van de categorie toont de diverse categorieën van uw taken in het linkerpaneel. Als u de kleur wilt wijzigen, definieert u de achtergrondkleur in `.category` element van het CSS-bestand.

## Taakcomponent {#task-component}

De taken worden getoond in het middelste paneel genoemd de Component TaskList. Als u de kleur van de stijl wilt wijzigen, wijzigt u de stijl die is gekoppeld aan de taakkiezer in de stijlpagina.
