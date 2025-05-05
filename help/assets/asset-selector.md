---
title: Asset Selector
description: Leer hoe u met de kiezer voor middelen metagegevens voor elementen in Adobe Experience Manager Assets kunt zoeken, filteren, doorbladeren en ophalen. Leer ook hoe u de interface van de elementenkiezer kunt aanpassen.
contentOwner: Adobe
feature: Asset Management,Metadata,Search
role: User
hide: true
exl-id: c84ce84a-1e52-48fd-a16c-38c7769df9af
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 1%

---

# Elementkiezer {#asset-selector}

>[!NOTE]
>
>De [ selecteur van Activa ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-selector.html?lang=nl-NL) werd genoemd [ plukker van Activa ](https://helpx.adobe.com/nl/experience-manager/6-2/assets/using/asset-picker.html) in vroegere versies van [!DNL Experience Manager].

Met de elementkiezer kunt u in [!DNL Adobe Experience Manager] Assets door elementen bladeren, zoeken en filteren. U kunt ook de metagegevens ophalen van elementen die u selecteert met de elementenkiezer. Als u de interface van de elementenkiezer wilt aanpassen, kunt u deze starten met ondersteunde aanvraagparameters. Met deze parameters wordt de context van de elementenkiezer voor een bepaald scenario ingesteld.

Momenteel, kunt u de verzoekparameters `assettype` (*Beeld/Video/Tekst*) en selectie `mode` (*Enige/Veelvoudige*) als contextuele informatie voor de activaselecteur overgaan, die door de selectie intact blijft.

De activaselecteur gebruikt het HTML5 **&#x200B;**&#x200B;bericht Window.postMessage om gegevens voor de geselecteerde activa naar de ontvanger te verzenden.

De assetkiezer is gebaseerd op de woordenlijst van de grondkiezer van Granite. De elementenkiezer werkt standaard in de modus Bladeren. U kunt echter filters toepassen met behulp van de ervaring van Omngonderzoek om uw zoekopdracht naar bepaalde elementen te verfijnen.

U kunt om het even welke Web-pagina (ongeacht of het deel van de container CQ) met de activaselecteur (`https://[AEM_server]:[port]/aem/assetpicker.html`) omvat.

## Contextafhankelijke parameters {#contextual-parameters}

U kunt de volgende aanvraagparameters in een URL doorgeven om de elementenkiezer in een bepaalde context te starten:

| Naam | Waarden | Voorbeeld | Doel |
|---|---|---|---|
| bronachtervoegsel (B) | De weg van de omslag als middelachtervoegsel in URL:`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | Als u de elementenkiezer wilt starten terwijl een bepaalde map is geselecteerd en de map `/content/dam/we-retail/en/activities` geselecteerd is, moet de URL de volgende vorm hebben: `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | Als u wilt dat een bepaalde map wordt geselecteerd wanneer de elementenkiezer wordt gestart, geeft u deze door als een bronachtervoegsel. |
| mode | enkelvoudig, meerdere | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | In meerdere modi kunt u meerdere elementen tegelijk selecteren met de elementkiezer. |
| dialoogvenster | true, false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | Gebruik deze parameters om de elementenkiezer te openen als granietdialoogvenster. Deze optie is alleen van toepassing wanneer u de elementenkiezer start via Granite Path Field en deze configureert als pickerSrc URL. |
| basis | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | Gebruik deze optie om de hoofdmap voor de elementenkiezer op te geven. In dit geval kunt u met de elementenkiezer alleen onderliggende elementen (direct/indirect) in de hoofdmap selecteren. |
| weergavemodus | zoeken |  | De elementenkiezer starten in de zoekmodus met parameters assettype en mimetype. |
| assettype (S) | afbeeldingen, documenten, multimedia, archieven | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives`</li> | Gebruik deze optie om elementtypen te filteren op basis van de doorgegeven waarde. |
| mimetype | mimetype(s) (`/jcr:content/metadata/dc:format`) van een element (jokerteken wordt ook ondersteund) | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker?viewmode=search&mimetype=*presentation&mimetype=*png`</li></ul> | Hiermee kunt u elementen filteren op basis van MIME-typen |

## De elementkiezer gebruiken {#using-the-asset-selector}

1. Ga naar `https://[AEM_server]:[port]/aem/assetpicker` als u de interface van de elementenkiezer wilt openen.
1. Navigeer naar de gewenste map en selecteer een of meer elementen.

   ![ chlimage_1-441 ](assets/chlimage_1-441.png)

   U kunt ook naar het gewenste element zoeken in het vak Universeel zoeken en het vervolgens selecteren.

   ![ chlimage_1-442 ](assets/chlimage_1-442.png)

   Als u via het vak UniverseelZoeken naar elementen zoekt, kunt u verschillende filters in het deelvenster **[!UICONTROL Filters]** selecteren om de zoekopdracht te verfijnen.

   ![ chlimage_1-443 ](assets/chlimage_1-443.png)

1. Klik op **[!UICONTROL Select]** op de werkbalk.

>[!MORELIKETHIS]
>
>* [ Micro-Frontend de Selector van Activa in AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-selector.html?lang=nl-NL)
