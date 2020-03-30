---
title: De indeling en positie van foutberichten van een adaptief formulier aanpassen
seo-title: De indeling en positie van foutberichten van een adaptief formulier aanpassen
description: 'U kunt de lay-out en de positie van de foutberichten van een adaptief for aanpassen. '
seo-description: 'U kunt de lay-out en de positie van de foutberichten van een adaptief for aanpassen. '
uuid: 6d3490f6-c867-44c9-a527-55f6d7221f99
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 136ac7e3-9d1f-4d58-bd4f-9dbe09eeafee
docset: aem65
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# De indeling en positie van foutberichten van een adaptief formulier aanpassen{#customize-layout-and-positioning-of-error-messages-of-an-adaptive-form}

U kunt de indeling en de positie van de foutberichten in een adaptief formulier aanpassen. U kunt de volgende aanpassingen uitvoeren:

* Locatie en lay-out van het bijschrift van een veld aanpassen zonder wijzigingen aan te brengen in de bijbehorende CSS-eigenschappen
* Positie van inline foutberichten aanpassen
* Inhoud van dynamische Help-indicator aanpassen
* De positie van de veldcomponenten (bijschrift, widget, korte beschrijving, lange beschrijving en Help-indicatorcomponenten) aanpassen zonder wijzigingen aan te brengen in de bijbehorende CSS-eigenschappen

## Lay-out van velden aanpassen {#customize-layout-of-fields}

U kunt de indeling van één veld of van alle velden aanpassen om de positie van bijschrift en foutberichten te wijzigen. Voer de volgende stappen uit om een aangepaste indeling toe te passen op een veld:

### Lay-out van één veld aanpassen {#customize-layout-of-a-single-field}

Voer de volgende stappen uit om een aangepaste indeling toe te passen op één veld:

1. Open het formulier in de modus **Stijl** . Als u het formulier wilt openen in de stijlmodus, tikt u op de paginaboolbalk op ![canvas-vervolgkeuzelijst](assets/canvas-drop-down.png) > **Stijl**.
1. Selecteer in het zijpaneel onder **Formulierobjecten** het veld en tik op de ![bewerkknop](assets/edit-button.png).
1. Selecteer de status van het veld dat u wilt aanpassen en geef de opmaak voor die status op.

   ![Inline opmaak van een veld opgeven](assets/edit-error-state.png)

### De indeling van alle velden van een formulier aanpassen {#customize-layout-of-all-the-fields-of-a-form}

Met AEM Forms kunt u nu een thema maken en dit toepassen op uw formulier. Met de Thema-editor kunt u op één plaats opmaak van formuliercomponenten opgeven. Wanneer u een thema maakt, geeft u de stijl op componentniveau op. Zie [Thema&#39;s in AEM-formulieren](../../forms/using/themes.md)voor meer informatie over thema&#39;s.

Maak een thema met de Thema-editor om de indeling van alle velden in het formulier aan te passen. Nadat u een thema hebt gemaakt, voert u de volgende stappen uit om het op een formulier toe te passen:

1. Open het formulier in de bewerkingsmodus.
1. Selecteer in de bewerkingsmodus een component, tik vervolgens op ![veldniveau](assets/field-level.png) > **Aangepaste formuliercontainer** en tik vervolgens op ![cmr](assets/cmppr.png).
1. Selecteer in het zijpaneel onder Adaptief formulierthema het thema dat u hebt gemaakt met de Thema-editor.

## Een aangepaste veldindeling maken {#create-a-custom-field-layout}

1. CRXDE-lijst openen. De standaard-URL is https://&#39;[server]:[port]&#39;/crx/de.
1. Kopieer een veldlay-out van het knooppunt /libs/fd/af/layouts/field (bijvoorbeeld defaultFieldLayout) naar het knooppunt /apps (bijvoorbeeld /apps/af-field-layout).
1. Wijzig de naam van het gekopieerde knooppunt en het bestand defaultFieldLayout.jsp. Bijvoorbeeld errorOnRight.jsp.

1. Waarde wijzigen van de eigenschappen qtip en jcr:description van het gekopieerde knooppunt. Wijzig bijvoorbeeld de waarde van de eigenschappen in Fout rechts

1. Om nieuwe stijlen en gedrag toe te voegen, creeer een cliëntbibliotheek in de /etc knoop.

   Creëer bijvoorbeeld op de locatie /etc/af-field-layout-clientlib de client-library van het knooppunt. Voeg de eigenschap Categorieën toe met het bestand value.field.errorOnRight en style.less met de volgende code:

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
1. Open het dialoogvenster Bewerken van het veld en selecteer het tabblad **Stijl** . Selecteer in het keuzemenu Veldlay-out **** configureren de nieuwe lay-out en klik op **OK**.

Het pakket ErrorOnRight.zip bevat code waarmee foutberichten aan de rechterkant van velden worden weergegeven.

[Bestand ophalen](assets/erroronright.zip)
