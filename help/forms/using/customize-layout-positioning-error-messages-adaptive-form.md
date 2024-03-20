---
title: De indeling en positie van foutberichten van een adaptief formulier aanpassen
description: U kunt de lay-out en de positie van de foutberichten van een adaptief for aanpassen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 5cb3ee55-f411-4692-84f7-89bf6ade729d
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
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

1. Open het formulier in **Stijl** -modus. Als u het formulier in de stijlmodus wilt openen, selecteert u op de paginaboolbalk de optie ![canvas-drop-down](assets/canvas-drop-down.png) > **Stijl**.
1. In de zijbalk, onder **Formulierobjecten**, selecteert u het veld en selecteert u de knop Bewerken ![bewerken, knop](assets/edit-button.png).
1. Selecteer de status van het veld dat u wilt aanpassen en geef de opmaak voor die status op.

   ![Inline opmaak van een veld opgeven](assets/edit-error-state.png)

### De indeling van alle velden van een formulier aanpassen {#customize-layout-of-all-the-fields-of-a-form}

Met AEM Forms kunt u nu een thema maken en dit toepassen op uw formulier. Met de Thema-editor kunt u de opmaak van formuliercomponenten op één locatie opgeven. Wanneer u een thema maakt, geeft u de stijl op componentniveau op. Zie voor meer informatie over thema&#39;s [Thema&#39;s in AEM Forms](../../forms/using/themes.md).

Maak een thema met de Thema-editor om de indeling van alle velden in het formulier aan te passen. Nadat u een thema hebt gemaakt, voert u de volgende stappen uit om het op een formulier toe te passen:

1. Open het formulier in de bewerkingsmodus.
1. Selecteer in de bewerkingsmodus een component en selecteer vervolgens ![op veldniveau](assets/field-level.png) > **Aangepaste formuliercontainer** en selecteer vervolgens ![cmppr](assets/cmppr.png).
1. Selecteer in het zijpaneel onder Adaptief formulierthema het thema dat u hebt gemaakt met de Thema-editor.

## Een aangepaste veldindeling maken {#create-a-custom-field-layout}

1. Open CRXDE Lite. De standaard-URL is https://&#39;[server]:[poort]...
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
1. Open het dialoogvenster Bewerken van het veld en selecteer de optie **Stijlen** tab. In de **Veldlay-out configureren** keuzelijst, selecteert u de nieuwe layout en klikt u op **OK**.

Het pakket ErrorOnRight.zip bevat code waarmee foutberichten aan de rechterkant van velden worden weergegeven.

[Bestand ophalen](assets/erroronright.zip)
