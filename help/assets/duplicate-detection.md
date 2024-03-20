---
title: Detectie van dubbele elementen inschakelen
description: Leer hoe u dubbele elementen in Experience Manager kunt detecteren.
contentOwner: AG
role: User, Admin
feature: Asset Management,Asset Reports
exl-id: a403d60e-2193-4835-8f37-4a40f2d01819
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---

# Detectie van dubbele elementen inschakelen {#enable-detection-of-duplicate-assets}

Als u probeert een middel te uploaden dat bestaat in [!DNL Adobe Experience Manager Assets], wordt de dubbele detectiefunctie geïdentificeerd als een duplicaat. Dubbele detectie is standaard uitgeschakeld. Voer de volgende stappen uit om de functie in te schakelen:

1. Open de [!DNL Experience Manager] Webconsole-configuratiepagina door toegang te krijgen tot `https://[aem_server]:[port]/system/console/configMgr`.
1. De configuratie van de servlet bewerken **[!UICONTROL Day CQ DAM Create Asset]**.
1. Selecteer de **[!UICONTROL detect duplicate]** en klik op **[!UICONTROL Save]**.

   ![Selecteer de optie Duplicaat detecteren in de servlet](assets/chlimage_1-377.png)

   *Afbeelding: selecteer de optie Dupliceren detecteren in het servlet.*

De functie Dupliceren detecteren is nu ingeschakeld in [!DNL Assets]. Wanneer een gebruiker een middel probeert te uploaden dat bestaat in [!DNL Experience Manager], controleert het systeem op conflict en wijst op het. De elementen worden geïdentificeerd met behulp van SHA-1-hash die is opgeslagen op `jcr:content/metadata/dam:sha1`, wat betekent dat dubbele elementen worden gedetecteerd, ongeacht de bestandsnamen.

>[!MORELIKETHIS]
>
>* [Dubbele middelen in bestaande opslagplaats (een zelfstudie van een lid van de gemeenschap)](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)
>* [Gedupliceerde elementen zoeken in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/detect-duplicate-assets.html)
