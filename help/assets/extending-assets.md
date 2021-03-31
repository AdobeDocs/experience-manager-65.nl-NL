---
title: Aanpassen en uitbreiden [!DNL Assets]
description: Leer manieren waarop u Asset Share en Asset Editor kunt aanpassen en uitbreiden, waarmee gebruikers een specifiek op maat gemaakte interface en een set functies krijgen.
contentOwner: AG
role: Developer
feature: Gereedschappen voor ontwikkelaars
translation-type: tm+mt
source-git-commit: 174e0703ae541641e3dc602e700bcd31624ae62c
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# [!DNL Assets] {#customizing-and-extending-assets} aanpassen en uitbreiden

De Asset Editor is het belangrijkste toegangspunt waarmee gebruikers van een Adobe Enterprise Manager-website de digitale middelen in uw opslagplaats kunnen zoeken, bekijken en bewerken.

Als ontwikkelaar [!DNL Experience Manager], kunt u de Redacteur van Activa op een aantal manieren aanpassen en uitbreiden, presenterend gebruikers met een specifiek op maat gemaakte interface en een reeks functionaliteit.

De volgende aspecten van de functionaliteit kunnen worden aangepast of verbeterd:

* [Editor van element uitbreiden](asseteditorx.md)
* [Zoeken naar elementen uitbreiden](searchx.md)
* [Middelen verwerken met behulp van mediafuncties en workflows](media-handlers.md)
* [Elementen integreren met activiteitsstroom](extending-activity-stream.md)
* [Ontwikkeling van proxy&#39;s](proxy.md)
* [Aanbevolen werkwijzen om ImageMagick te configureren](best-practices-for-imagemagick.md)

## De weergave aanpassen {#customizing-the-look-and-feel}

De volgende aspecten van de vormgeving van de Asset Editor kunnen worden aangepast:

* Logo: U kunt het logo van uw eigen organisatie aan de interface toevoegen.
* Kleuren en lettertypen: U kunt de kleuren en lettertypen wijzigen die in de interface worden gebruikt.
* HTML-code: Voor een grondiger aanpassing kunt u de onderliggende HTML-code wijzigen die de interfaces definieert.

## Uitvoeringen aanpassen {#customizing-renditions}

In de terminologie [!DNL Experience Manager Assets] is een vertoning de vorm waarin een element wordt gepresenteerd. In het algemeen kan een bepaald actief meerdere uitvoeringen hebben. Zo kan de oorspronkelijke grootte van een kleurenafbeelding bijvoorbeeld één uitvoering hebben, een andere bij een verkleind formaat en een andere afbeelding die wordt verkleind en omgezet in grijswaarden.

De uitvoeringen waarin een bepaald element beschikbaar is, kunnen worden aangepast en nieuwe uitvoeringen worden gemaakt.
