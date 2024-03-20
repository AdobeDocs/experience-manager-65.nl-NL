---
title: Aanpassen en uitbreiden [!DNL Assets]
description: Leer manieren waarop u Asset Share en Asset Editor kunt aanpassen en uitbreiden, waarmee gebruikers een specifiek op maat gemaakte interface en een set functies krijgen.
contentOwner: AG
role: Developer
feature: Developer Tools
exl-id: 0271c528-23b0-4a3a-b5e8-5baf6cdeecc7
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Aanpassen en uitbreiden [!DNL Assets] {#customizing-and-extending-assets}

De Asset Editor is het belangrijkste toegangspunt dat gebruikers van een Adobe Enterprise Manager-website gebruiken om de digitale middelen in uw opslagplaats te zoeken, weer te geven en te manipuleren.

Als [!DNL Experience Manager] ontwikkelaar, kunt u de Redacteur van Activa op verscheidene manieren aanpassen en uitbreiden, presenterend gebruikers met een specifiek op maat gemaakte interface en een reeks functionaliteit.

De volgende aspecten van de functionaliteit kunnen worden aangepast of verbeterd:

* [Editor van element uitbreiden](asseteditorx.md)
* [Zoeken naar elementen uitbreiden](searchx.md)
* [Middelen verwerken met behulp van mediafuncties en workflows](media-handlers.md)
* [Elementen integreren met activiteitsstroom](extending-activity-stream.md)
* [Ontwikkeling van proxy&#39;s voor elementen](proxy.md)
* [Aanbevolen werkwijzen om ImageMagick te configureren](best-practices-for-imagemagick.md)

## De weergave aanpassen {#customizing-the-look-and-feel}

De volgende aspecten van de vormgeving van de Asset Editor kunnen worden aangepast:

* Logo: u kunt het logo van uw eigen organisatie aan de interface toevoegen.
* Kleuren en lettertypen: u kunt de kleuren en lettertypen wijzigen die in de interface worden gebruikt.
* HTML Code: voor grondigere aanpassing kunt u de onderliggende HTML code wijzigen die de interfaces definieert.

## Uitvoeringen aanpassen {#customizing-renditions}

In [!DNL Experience Manager Assets] terminologie een uitvoering is de vorm waarin een actief wordt gepresenteerd. In het algemeen kan een bepaald actief meerdere uitvoeringen hebben. Zo kan de oorspronkelijke grootte van een kleurenafbeelding bijvoorbeeld één uitvoering hebben, een andere bij een verkleind formaat en een andere afbeelding die wordt verkleind en omgezet in grijswaarden.

De uitvoeringen waarin een bepaald element beschikbaar is, kunnen worden aangepast en nieuwe uitvoeringen worden gemaakt.
