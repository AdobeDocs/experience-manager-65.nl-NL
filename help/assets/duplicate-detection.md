---
title: Detectie van dubbele elementen inschakelen
description: Leer hoe u dubbele elementen in Experience Manager kunt detecteren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---


# Detectie van dubbele elementen inschakelen {#enable-detection-of-duplicate-assets}

Als u probeert een element te uploaden waarin [!DNL Adobe Experience Manager Assets]zich bevindt, wordt dit door de functie voor dubbele detectie geïdentificeerd als gedupliceerd. Dubbele detectie is standaard uitgeschakeld. Voer de volgende stappen uit om de functie in te schakelen:

1. Open de de configuratiepagina van de [!DNL Experience Manager] Console van het Web door toegang tot `https://[aem_server]:[port]/system/console/configMgr`.
1. Bewerk de configuratie voor de servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Selecteer de **[!UICONTROL detect duplicate]** optie en klik op **[!UICONTROL Save]**.

   ![Selecteer de optie Duplicaat detecteren in de servlet](assets/chlimage_1-377.png)

   *Afbeelding: Selecteer dubbele optie in servlet ontdekken.*

De functie Dupliceren detecteren is nu ingeschakeld in [!DNL Assets]. Wanneer een gebruiker een middel probeert te uploaden dat binnen bestaat [!DNL Experience Manager], controleert het systeem op conflict en wijst op het. De elementen worden geïdentificeerd met behulp van SHA-1-hash opgeslagen op `jcr:content/metadata/dam:sha1`, wat betekent dat dubbele elementen worden gedetecteerd, ongeacht de bestandsnamen.

>[!MORELIKETHIS]
>
>* [Dubbele middelen in bestaande opslagplaats (een zelfstudie van een lid van de gemeenschap)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

