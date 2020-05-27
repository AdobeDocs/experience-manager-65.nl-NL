---
title: Detectie van dubbele elementen inschakelen
description: Leer hoe u dubbele elementen kunt detecteren in Experience Manager.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---


# Detectie van dubbele elementen inschakelen {#enable-detection-of-duplicate-assets}

Als u probeert middelen te uploaden die in de Middelen van de Manager van de Ervaring van Adobe bestaan, identificeert de dubbele opsporingseigenschap het als dubbel. Dubbele detectie is standaard uitgeschakeld. Voer de volgende stappen uit om de functie in te schakelen:

1. Open de pagina van de Configuratie van de Console van het Web van de Manager van de Ervaring door toegang te hebben tot `https://[aem_server]:[port]/system/console/configMgr`.
1. Bewerk de configuratie voor de servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Selecteer de **[!UICONTROL detect duplicate]** optie en klik op **[!UICONTROL Save]**.

   ![Selecteer de optie Duplicaat detecteren in de servlet](assets/chlimage_1-377.png)

   *Afbeelding: Selecteer de optie Duplicaat detecteren in de servlet*

De functie Dupliceren detecteren is nu ingeschakeld in Middelen. Wanneer een gebruiker een middel probeert te uploaden dat in de Manager van de Ervaring bestaat, controleert het systeem op conflict en wijst op het. De elementen worden geïdentificeerd met behulp van SHA-1-hash opgeslagen op `jcr:content/metadata/dam:sha1`, wat betekent dat dubbele elementen worden gedetecteerd, ongeacht de bestandsnamen.

>[!MORELIKETHIS]
>
>* [Dubbele middelen in bestaande opslagplaats (een zelfstudie van een lid van de gemeenschap)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

