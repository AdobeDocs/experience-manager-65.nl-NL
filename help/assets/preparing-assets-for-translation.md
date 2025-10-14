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

In [!DNL Adobe Experience Manager Assets] worden meertalige middelen opgenomen in mappen, waarbij elke map de elementen in een andere taal bevat.

Elke taalmap wordt een taalkopie genoemd. De hoofdmap van een taalkopie, de hoofdtaal genoemd, identificeert de taal van de inhoud in de taalkopie. Bijvoorbeeld, */content/dam/it* is de Italiaanse taalwortel voor het Italiaans taalexemplaar. De exemplaren van de taal moeten a [&#x200B; correct gevormde taalwortel &#x200B;](preparing-assets-for-translation.md#creating-a-language-root) gebruiken zodat de correcte taal wordt gericht wanneer de vertalingen van bronactiva worden uitgevoerd.

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

1. Maak de hoofdtaal van uw primaire taal. De hoofdmap voor de Engelse taal in de voorbeeldmaphiërarchie is bijvoorbeeld `/content/dam/en` . Zorg ervoor dat de taalwortel correct volgens de informatie in [&#x200B; wordt gevormd creeer een Wortel van de Taal &#x200B;](preparing-assets-for-translation.md#creating-a-language-root).

1. Voeg elementen toe aan uw primaire taal.
1. Creeer de taalwortel van elke doeltaal waarvoor u een taalexemplaar vereist.

## Een hoofdmap voor talen maken {#creating-a-language-root}

Als u de hoofdmap van de taal wilt maken, maakt u een map en gebruikt u een ISO-taalcode als waarde voor de eigenschap Naam. Nadat u de hoofdmap van de taal hebt gemaakt, kunt u op elk niveau in de hoofdmap van de taal een kopie van de taal maken.

De hoofdpagina van de Italiaanse taalkopie van de voorbeeldhiërarchie heeft bijvoorbeeld `it` als de eigenschap Naam. Het bezit van de Naam wordt gebruikt als naam van de activaknoop in de bewaarplaats, en bepaalt daarom de weg van de activa. (`https://[aem_server]:[port]/assets.html/content/dam/it/`).

1. Klik in de [!DNL Assets] -console op **[!UICONTROL Create]** en kies **[!UICONTROL Folder]** in het menu.

   ![&#x200B; creeer omslag &#x200B;](assets/Create-folder.png)

1. Typ in het veld **[!UICONTROL Name]** de landcode in de notatie `<language-code>` .

   ![&#x200B; voeg taalcode in omslag &#x200B;](assets/Add-language-code-in-folder.png) toe

1. Klik op **[!UICONTROL Create]**. De taalhoofdmap wordt gemaakt in de [!DNL Assets] -console.

## Taalwortels weergeven {#viewing-language-roots}

De interface [!DNL Experience Manager] biedt een deelvenster **[!UICONTROL References]** met een lijst met taalwortels die binnen [!DNL Assets] zijn gemaakt.

1. Selecteer in de [!DNL Assets] -console de primaire taal waarvoor u taalkopieën wilt maken.
1. Selecteer de optie **[!UICONTROL References]** in het linkerspoor om het deelvenster [!UICONTROL Reference] te openen.

   ![&#x200B; chlimage_1-122 &#x200B;](assets/chlimage_1-122.png)

1. Klik in het venster Referenties op **[!UICONTROL Language Copies]** . In het deelvenster [!UICONTROL Language Copies] worden de taalkopieën van de elementen weergegeven.

   ![&#x200B; taalexemplaren &#x200B;](assets/lang-copy2.png)
