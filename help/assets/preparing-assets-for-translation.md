---
title: Elementen voorbereiden voor vertaling
description: Maak hoofdmappen voor talen om elementen voor te bereiden voor vertaling ter ondersteuning van meertalige middelen.
contentOwner: AG
role: User, Admin
feature: Projects
exl-id: eee768e3-3eb4-46fa-b9ae-9ef8764a3a94
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Elementen voorbereiden voor vertaling {#preparing-assets-for-translation}

Meertalige elementen zijn elementen met binaire getallen, metagegevens en tags in meerdere talen. Over het algemeen bestaan binaire bestanden, metagegevens en tags voor elementen in één taal, die vervolgens naar andere talen worden vertaald voor gebruik in meertalige projecten.

In [!DNL Adobe Experience Manager Assets]Meertalige middelen worden opgenomen in mappen, waarbij elke map de middelen in een andere taal bevat.

Elke taalmap wordt een taalkopie genoemd. De hoofdmap van een taalkopie, de hoofdtaal genoemd, identificeert de taal van de inhoud in de taalkopie. Bijvoorbeeld: */content/dam/it* is de Italiaanse taalbasis voor de Italiaanse taalkopie. Taalkopieën moeten een [correct gevormde taalwortel](preparing-assets-for-translation.md#creating-a-language-root) zodat de juiste taal wordt gebruikt wanneer vertalingen van bronelementen worden uitgevoerd.

Het taalexemplaar waarvoor u oorspronkelijk activa toevoegt is de primaire taal. De primaire taal is de bron die in andere talen wordt vertaald. Een voorbeeld van een maphiërarchie bevat verschillende taalwortels:

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

1. Maak de hoofdtaal van uw primaire taal. De hoofdmap van de kopie van de Engelse taal in de voorbeeldmaphiërarchie is bijvoorbeeld `/content/dam/en`. Zorg ervoor dat de taalwortel correct volgens de informatie in wordt gevormd [Een hoofdmap voor talen maken](preparing-assets-for-translation.md#creating-a-language-root).

1. Voeg elementen toe aan uw primaire taal.
1. Creeer de taalwortel van elke doeltaal waarvoor u een taalexemplaar vereist.

## Een hoofdmap voor talen maken {#creating-a-language-root}

Als u de hoofdmap van de taal wilt maken, maakt u een map en gebruikt u een ISO-taalcode als waarde voor de eigenschap Naam. Nadat u de hoofdmap van de taal hebt gemaakt, kunt u op elk niveau in de hoofdmap van de taal een kopie van de taal maken.

De hoofdpagina van de Italiaanse taalkopie van de voorbeeldhiërarchie heeft bijvoorbeeld `it` als de eigenschap Name. Het bezit van de Naam wordt gebruikt als naam van de activaknoop in de bewaarplaats, en bepaalt daarom de weg van de activa. (`https://[aem_server]:[port]/assets.html/content/dam/it/`).

1. Van de [!DNL Assets] console, klik **[!UICONTROL Create]** en kiest u **[!UICONTROL Folder]** in het menu.

   ![Map maken](assets/Create-folder.png)

1. In de **[!UICONTROL Name]** veldtype de landcode in het formaat `<language-code>`.

   ![Taalcode toevoegen in map](assets/Add-language-code-in-folder.png)

1. Klik op **[!UICONTROL Create]**. De taalhoofdmap wordt gemaakt in het dialoogvenster [!DNL Assets] console.

## Taalwortels weergeven {#viewing-language-roots}

[!DNL Experience Manager] interface biedt een **[!UICONTROL References]** deelvenster met een lijst met taalbasisprincipes die zijn gemaakt in [!DNL Assets].

1. In de [!DNL Assets] -console, selecteert u de primaire taal waarvoor u taalkopieën wilt maken.
1. Selecteer in het linkerspoor de optie **[!UICONTROL References]** om de [!UICONTROL Reference] venster.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. Klik in het venster Referenties op **[!UICONTROL Language Copies]**. De [!UICONTROL Language Copies] toont de taalexemplaren van de elementen.

   ![taalkopieën](assets/lang-copy2.png)
