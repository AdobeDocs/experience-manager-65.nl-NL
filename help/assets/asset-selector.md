---
title: Asset Selector
description: Leer hoe u met de kiezer voor middelen metagegevens voor elementen in Adobe Experience Manager Assets kunt zoeken, filteren, doorbladeren en ophalen. Leer ook hoe u de interface van de elementenkiezer kunt aanpassen.
contentOwner: AG
feature: Asset Management,Metadata,Search
role: User
exl-id: 4b518ac0-5b8b-4d61-ac31-269aa1f5abe4
source-git-commit: 4139b42d5cd3d7d1d93863dc07cfafd58c3f64f2
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Elementkiezer {#asset-selector}

>[!NOTE]
>
>De Asset-kiezer is aangeroepen [Elementkiezer](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html) in eerdere versies van [!DNL Experience Manager].

Met de elementkiezer kunt u elementen zoeken, zoeken en filteren in [!DNL Adobe Experience Manager] Elementen. U kunt ook de metagegevens ophalen van elementen die u selecteert met de elementenkiezer. Als u de interface van de elementenkiezer wilt aanpassen, kunt u deze starten met ondersteunde aanvraagparameters. Met deze parameters wordt de context van de elementenkiezer voor een bepaald scenario ingesteld.

Momenteel kunt u de parameters voor aanvragen doorgeven `assettype` (*Afbeelding/Video/Tekst*) en selectie `mode` (*Enkel/Meerdere*) als contextuele informatie voor de elementenkiezer, die tijdens de selectie intact blijft.

De elementkiezer gebruikt de HTML5 **Window.postMessage** bericht om gegevens voor het geselecteerde element naar de ontvanger te verzenden.

De assetkiezer is gebaseerd op de woordenlijst van de grondkiezer van Granite. De elementenkiezer werkt standaard in de modus Bladeren. U kunt echter filters toepassen met behulp van de ervaring van Omngonderzoek om uw zoekopdracht naar bepaalde elementen te verfijnen.

U kunt elke webpagina (ongeacht of deze deel uitmaakt van de CQ-container) integreren met de elementenkiezer (`https://[AEM_server]:[port]/aem/assetpicker.html`).

## Contextafhankelijke parameters {#contextual-parameters}

U kunt de volgende aanvraagparameters in een URL doorgeven om de elementenkiezer in een bepaalde context te starten:

| Naam | Waarden | Voorbeeld | Doel |
|---|---|---|---|
| bronachtervoegsel (B) | Mappad als resix van de bron in de URL:`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | De elementkiezer starten met een bepaalde map geselecteerd, bijvoorbeeld met de map `/content/dam/we-retail/en/activities` geselecteerd, moet de URL de volgende vorm hebben: `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | Als u wilt dat een bepaalde map wordt geselecteerd wanneer de elementenkiezer wordt gestart, geeft u deze door als een bronachtervoegsel. |
| mode | enkelvoudig, meerdere | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | In meerdere modi kunt u meerdere elementen tegelijk selecteren met de elementkiezer. |
| dialoogvenster | true, false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | Gebruik deze parameters om de elementenkiezer te openen als granietdialoogvenster. Deze optie is alleen van toepassing wanneer u de elementenkiezer start via Granite Path Field en deze configureert als pickerSrc URL. |
| basis | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | Gebruik deze optie om de hoofdmap voor de elementenkiezer op te geven. In dit geval kunt u met de elementenkiezer alleen onderliggende elementen (direct/indirect) in de hoofdmap selecteren. |
| viewmode | zoeken |  | De elementenkiezer starten in de zoekmodus met parameters assettype en mimetype. |
| assettype (S) | afbeeldingen, documenten, multimedia, archieven | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives`</li> | Gebruik deze optie om elementtypen te filteren op basis van de doorgegeven waarde. |
| mimetype | mimetype(s) (`/jcr:content/metadata/dc:format`) van een element (jokerteken wordt ook ondersteund) | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker?viewmode=search&mimetype=*presentation&mimetype=*png`</li></ul> | Hiermee kunt u elementen filteren op basis van MIME-typen |

## De elementkiezer gebruiken {#using-the-asset-selector}

1. Ga naar `https://[AEM_server]:[port]/aem/assetpicker`.
1. Navigeer naar de gewenste map en selecteer een of meer elementen.

   ![chlimage_1-441](assets/chlimage_1-441.png)

   U kunt ook naar het gewenste element zoeken in het vak Universeel zoeken en het vervolgens selecteren.

   ![chlimage_1-442](assets/chlimage_1-442.png)

   Als u via het vak UniverseelZoeken naar elementen zoekt, kunt u verschillende filters selecteren in het menu **[!UICONTROL Filters]** om uw zoekopdracht te verfijnen.

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. Tikken/klikken **[!UICONTROL Select]** op de werkbalk.
