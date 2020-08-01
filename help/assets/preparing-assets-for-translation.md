---
title: Elementen voorbereiden voor vertaling
description: Maak hoofdmappen voor talen om elementen voor te bereiden voor vertaling ter ondersteuning van meertalige middelen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Elementen voorbereiden voor vertaling {#preparing-assets-for-translation}

Meertalige elementen zijn elementen met binaire getallen, metagegevens en tags in meerdere talen. Over het algemeen bestaan binaire bestanden, metagegevens en tags voor elementen in één taal, die vervolgens naar andere talen worden vertaald voor gebruik in meertalige projecten.

In [!DNL Adobe Experience Manager Assets]mappen worden meertalige middelen opgenomen, waarbij elke map de middelen in een andere taal bevat.

Elke taalmap wordt een taalkopie genoemd. De hoofdmap van een taalkopie, de hoofdtaal genoemd, identificeert de taal van de inhoud in de taalkopie. Bijvoorbeeld: */content/dam/it* is de Italiaanse taalbasis voor de Italiaanse taalkopie. De exemplaren van de taal moeten een [correct-gevormde taalwortel](preparing-assets-for-translation.md#creating-a-language-root) gebruiken zodat de correcte taal wordt gericht wanneer de vertalingen van bronactiva worden uitgevoerd.

De taalkopie waarvoor u oorspronkelijk elementen toevoegt, is de primaire taal. De primaire taal is de bron die in andere talen wordt vertaald. Een voorbeeld van een maphiërarchie bevat verschillende taalwortels:

```
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

1. Maak de hoofdtaalhoofdmap van uw primaire taal. De hoofdmap voor de Engelse taal in de voorbeeldmaphiërarchie is bijvoorbeeld `/content/dam/en`. Zorg ervoor dat de hoofdmap van de taal correct is geconfigureerd volgens de informatie in [Een hoofdmap](preparing-assets-for-translation.md#creating-a-language-root)maken.

1. Voeg middelen toe aan uw primaire taal.
1. Creeer de taalwortel van elke doeltaal waarvoor u een taalexemplaar vereist.

## Een hoofdmap voor talen maken {#creating-a-language-root}

Als u de hoofdmap van de taal wilt maken, maakt u een map en gebruikt u een ISO-taalcode als waarde voor de eigenschap Naam. Nadat u de hoofdtaal hebt gemaakt, kunt u op elk niveau in de hoofdmap van de taal een kopie van de taal maken.

De hoofdpagina van de Italiaanse taalkopie van de voorbeeldhiërarchie heeft bijvoorbeeld de eigenschap Naam `it` . Het bezit van de Naam wordt gebruikt als naam van de activaknoop in de bewaarplaats, en bepaalt daarom de weg van de activa. (`https://[aem_server]:[port]/assets.html/content/dam/it/`).

1. From the [!DNL Assets] console, click **[!UICONTROL Create]** and choose **[!UICONTROL Folder]** from the menu.

   ![Map maken](assets/Create-folder.png)

1. Typ in het **[!UICONTROL Name]** veld de landcode in de notatie `<language-code>`.

   ![Taalcode toevoegen in map](assets/Add-language-code-in-folder.png)

1. Klik op **[!UICONTROL Create]**. De taalwortel wordt gecreeerd in de [!DNL Assets] console.

## Taalwortels weergeven {#viewing-language-roots}

[!DNL Experience Manager] de interface verstrekt een **[!UICONTROL References]** paneel dat een lijst van taalwortels toont die binnen zijn gecreeerd [!DNL Assets].

1. Selecteer in de [!DNL Assets] console de primaire taal waarvoor u taalkopieën wilt maken.
1. Selecteer in het linkerspoor de **[!UICONTROL References]** optie om het [!UICONTROL Reference] venster te openen.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. Klik in het venster Referenties op **[!UICONTROL Language Copies]**. In het [!UICONTROL Language Copies] deelvenster worden de taalkopieën van de elementen weergegeven.

   ![taalkopieën](assets/lang-copy2.png)
