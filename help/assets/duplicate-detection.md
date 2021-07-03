---
title: Detectie van dubbele elementen inschakelen
description: Leer hoe u dubbele elementen in Experience Manager kunt detecteren.
contentOwner: AG
role: User, Admin
feature: Middelenbeheer, Asset Reports
exl-id: a403d60e-2193-4835-8f37-4a40f2d01819
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---

# Detectie van dubbele elementen inschakelen {#enable-detection-of-duplicate-assets}

Als u probeert een middel te uploaden dat in [!DNL Adobe Experience Manager Assets] bestaat, identificeert de dubbele opsporingseigenschap het als duplicaat. Dubbele detectie is standaard uitgeschakeld. Voer de volgende stappen uit om de functie in te schakelen:

1. Open de [!DNL Experience Manager] de configuratiepagina van de Console van het Web door tot `https://[aem_server]:[port]/system/console/configMgr` toegang te hebben.
1. Bewerk de configuratie voor de servlet **[!UICONTROL Day CQ DAM Create Asset]**.
1. Selecteer de optie **[!UICONTROL detect duplicate]** en klik op **[!UICONTROL Save]**.

   ![Selecteer de optie Duplicaat detecteren in de servlet](assets/chlimage_1-377.png)

   *Afbeelding: Selecteer dubbele optie in servlet ontdekken.*

De functie voor het opsporen van dubbele gegevens is nu ingeschakeld in [!DNL Assets]. Wanneer een gebruiker een middel probeert te uploaden dat in [!DNL Experience Manager] bestaat, controleert het systeem op conflict en wijst op het. De elementen worden geïdentificeerd met behulp van SHA-1-hash die is opgeslagen op `jcr:content/metadata/dam:sha1`. Dit betekent dat dubbele elementen worden gedetecteerd, ongeacht de bestandsnamen.

>[!MORELIKETHIS]
>
>* [Dubbele middelen in bestaande opslagplaats (een zelfstudie van een lid van de gemeenschap)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)

