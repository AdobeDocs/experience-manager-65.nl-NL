---
title: Elementen voorbereiden voor vertaling
description: Maak hoofdmappen voor talen om elementen voor te bereiden voor vertaling ter ondersteuning van meertalige middelen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1d3e908eafa1cdcbc6ef557da509f12cdd9418cc
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Elementen voorbereiden voor vertaling {#preparing-assets-for-translation}

Meertalige elementen zijn elementen met binaire getallen, metagegevens en tags in meerdere talen. Over het algemeen bestaan binaire bestanden, metagegevens en tags voor elementen in één taal, die vervolgens naar andere talen worden vertaald voor gebruik in meertalige projecten.

In [!DNL Adobe Experience Manager Assets] worden meertalige middelen opgenomen in mappen, waarbij elke map de middelen in een andere taal bevat.

Elke taalmap wordt een taalkopie genoemd. De hoofdmap van een taalkopie, de hoofdmap van de taal genoemd, identificeert de taal van de inhoud in de taalkopie. */content/dam/it* is bijvoorbeeld de Italiaanse taalhoofdmap voor de Italiaanse taalkopie. De exemplaren van de taal moeten [correct-gevormde taalwortel](preparing-assets-for-translation.md#creating-a-language-root) gebruiken zodat de correcte taal wordt gericht wanneer de vertalingen van bronactiva worden uitgevoerd.

De taalkopie waarvoor u oorspronkelijk elementen toevoegt, is de primaire taal. De primaire taal is de bron die in andere talen wordt vertaald. Een voorbeeld van een maphiërarchie bevat verschillende taalwortels:

```shell
/content
    /- dam
        |- en
        |- fr
        |- de
        |- es
        |- it
        |- ja
        |- zh
```

Voer de volgende stappen uit om uw middelen voor vertaling voor te bereiden:

1. Maak de hoofdtaalhoofdmap van uw primaire taal. De hoofdmap van de Engelse taalkopie in de hiërarchie van de voorbeeldmap is bijvoorbeeld `/content/dam/en`. Zorg ervoor dat de taalwortel correct volgens de informatie in [creeer een Wortel van de Taal](preparing-assets-for-translation.md#creating-a-language-root) wordt gevormd.

1. Voeg middelen toe aan uw primaire taal.
1. Creeer de taalwortel van elke doeltaal waarvoor u een taalexemplaar vereist.

## Een hoofdtaalmap {#creating-a-language-root} maken

Als u de hoofdmap van de taal wilt maken, maakt u een map en gebruikt u een ISO-taalcode als waarde voor de eigenschap Naam. Nadat u de hoofdtaal hebt gemaakt, kunt u op elk niveau in de hoofdmap van de taal een kopie van de taal maken.

De basispagina van de Italiaanse taalkopie van de voorbeeldhiërarchie heeft bijvoorbeeld `it` als eigenschap Name. Het bezit van de Naam wordt gebruikt als naam van de activaknoop in de bewaarplaats, en bepaalt daarom de weg van de activa. (`https://[aem_server]:[port]/assets.html/content/dam/it/`).

1. Klik in de [!DNL Assets]-console op **[!UICONTROL Create]** en kies **[!UICONTROL Folder]** in het menu.

   ![Map maken](assets/Create-folder.png)

1. Typ in het veld **[!UICONTROL Name]** de landcode in de notatie `<language-code>`.

   ![Taalcode toevoegen in map](assets/Add-language-code-in-folder.png)

1. Klik op **[!UICONTROL Create]**. De taalwortel wordt gecreeerd in de [!DNL Assets] console.

## Taalwortels {#viewing-language-roots} weergeven

[!DNL Experience Manager] de interface verstrekt een  **[!UICONTROL References]** paneel dat een lijst van taalwortels toont die binnen zijn gecreeerd  [!DNL Assets].

1. Selecteer in de [!DNL Assets]-console de primaire taal waarvoor u taalkopieën wilt maken.
1. Selecteer **[!UICONTROL References]** optie in de linkertrack om het [!UICONTROL Reference]-venster te openen.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. Klik in het venster Referenties op **[!UICONTROL Language Copies]**. In het deelvenster [!UICONTROL Language Copies] worden de taalkopieën van de elementen weergegeven.

   ![taalkopieën](assets/lang-copy2.png)
