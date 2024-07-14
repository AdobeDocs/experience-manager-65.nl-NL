---
title: De indeling en positie van foutberichten van een adaptief formulier aanpassen
description: U kunt de lay-out en de positie van de foutberichten van een adaptief for aanpassen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 5cb3ee55-f411-4692-84f7-89bf6ade729d
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
source-git-commit: 8a77756e8ba771c8de9950c2323bef8f23cc59b4
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# De indeling en positie van foutberichten van een adaptief formulier aanpassen{#customize-layout-and-positioning-of-error-messages-of-an-adaptive-form}

U kunt de indeling en de positie van de foutberichten van een adaptief formulier aanpassen. U kunt de volgende aanpassingen uitvoeren:

* De locatie en lay-out van het bijschrift van een veld aanpassen zonder de bijbehorende CSS-eigenschappen te wijzigen
* De positie van inline-foutberichten aanpassen
* Inhoud van dynamische Help-indicator aanpassen
* De positie van de veldcomponenten (bijschrift, widget, korte beschrijving, lange beschrijving en Help-indicatorcomponenten) aanpassen zonder de bijbehorende CSS-eigenschappen te wijzigen

## Lay-out van velden aanpassen {#customize-layout-of-fields}

U kunt de indeling van één veld of van alle velden aanpassen om de positie van bijschrift en foutberichten te wijzigen.

Ga als volgt te werk om een aangepaste indeling toe te passen op een veld:

### Lay-out van één veld aanpassen {#customize-layout-of-a-single-field}

1. Open de vorm op **wijze van de Stijl**. Om de vorm op stijlwijze te openen, op de paginaboolbar selecteren ![ canvas-drop-down ](assets/canvas-drop-down.png) > **Stijl**.
1. In sidebar, onder **Objecten van de Vorm**, selecteer het gebied en selecteer uitgeven knoop ![ uitgeven-knoop ](assets/edit-button.png).
1. Selecteer de status van het veld dat u wilt aanpassen en geef de opmaak voor die status op.

   ![ het specificeren van gealigneerde het stileren van een gebied ](assets/edit-error-state.png)

### De indeling van alle velden van een formulier aanpassen {#customize-layout-of-all-the-fields-of-a-form}

Met AEM Forms kunt u nu een thema maken en dit toepassen op uw formulier. Met de Thema-editor kunt u de opmaak van formuliercomponenten op één locatie opgeven. Wanneer u een thema maakt, geeft u de stijl op componentniveau op. Voor meer informatie over thema&#39;s, zie [ Thema&#39;s in AEM Forms ](../../forms/using/themes.md).

Maak een thema met de Thema-editor om de indeling van alle velden in het formulier aan te passen. Nadat u een thema hebt gemaakt, voert u de volgende stappen uit om het op een formulier toe te passen:

1. Open het formulier in de bewerkingsmodus.
1. Op geef wijze uit, selecteer een component, dan uitgezocht ![ gebied-niveau ](assets/field-level.png) > **Aangepaste Container van de Vorm**, en selecteer dan ![ cmp ](assets/cmppr.png).
1. Selecteer in het zijpaneel onder Adaptief formulierthema het thema dat u hebt gemaakt met de Thema-editor.

## Een aangepaste veldindeling maken {#create-a-custom-field-layout}

1. Open CRXDE Lite. Het gebrek URL is https://&#39; [ server ]:[ haven ]&#39;/crx/de.
1. Kopieer een veldindeling van het knooppunt /libs/fd/af/layouts/field (bijvoorbeeld defaultFieldLayout) naar het knooppunt /apps (bijvoorbeeld /apps/af-field-layout).
1. Wijzig de naam van het gekopieerde knooppunt en het bestand defaultFieldLayout.jsp. Bijvoorbeeld errorOnRight.jsp.

1. Wijzig de waarde van de eigenschappen qtip en jcr:description van het gekopieerde knooppunt. Wijzig bijvoorbeeld de waarde van de eigenschappen in Fout rechts

1. Om nieuwe stijlen en gedrag toe te voegen, creeer een cliëntbibliotheek in de /etc knoop.

   Maak bijvoorbeeld op de locatie /etc/af-field-layout-clientlib de client-library van het knooppunt. Voeg de eigenschap Categorieën toe met het bestand value.field.errorOnRight en style.less met de volgende code:

   ```css
   .widgetErrorWrapper {
   
    height: 38px;
    margin: 5px;
   
    .guideFieldWidget{
    width: 60%;
    float: left; 
    }
   
    .guideFieldError{
    overflow:hidden;
    width:40%; 
    }
   
   }
   ```

1. Als u de weergave en het gedrag wilt verbeteren, neemt u de clientbibliotheek op die in het lay-outbestand is gemaakt (errorOnRight.jsp).
1. Open uitgeven dialoogdoos van het gebied en selecteer **het Stijlen** tabel. In **vorm de drop-down doos van de Lay-out van het Gebied**, selecteer de pas gecreëerde lay-out, en klik **O.K.**.

Het pakket ErrorOnRight.zip bevat code waarmee foutberichten aan de rechterkant van velden worden weergegeven.

[Bestand ophalen](assets/erroronright.zip)
