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

Als u probeert een element te uploaden dat voorkomt in [!DNL Adobe Experience Manager Assets] , wordt dit door de functie voor dubbele detectie geïdentificeerd als gedupliceerd. Dubbele detectie is standaard uitgeschakeld. Voer de volgende stappen uit om de functie in te schakelen:

1. Open de [!DNL Experience Manager] webconsoleconfiguratiepagina door `https://[aem_server]:[port]/system/console/configMgr` te openen.
1. Bewerk de configuratie voor de servlet **[!UICONTROL Day CQ DAM Create Asset]** .
1. Selecteer de optie **[!UICONTROL detect duplicate]** en klik op **[!UICONTROL Save]** .

   ![&#x200B; Uitgezocht ontdekt dubbele optie in servlet &#x200B;](assets/chlimage_1-377.png)

   *Cijfer: Selecteer ontdekt dubbele optie in servlet.*

De functie Dupliceren detecteren is nu ingeschakeld in [!DNL Assets] . Wanneer een gebruiker een middel probeert te uploaden dat in [!DNL Experience Manager] bestaat, controleert het systeem op conflict en wijst het erop. De elementen worden geïdentificeerd met behulp van SHA-1-hash die is opgeslagen bij `jcr:content/metadata/dam:sha1` . Dit betekent dat dubbele elementen worden gedetecteerd, ongeacht de bestandsnamen.

>[!MORELIKETHIS]
>
>* [&#x200B; Dupliceer activa in bestaande bewaarplaats (een leerprogramma van een communautair lid) &#x200B;](https://experience-aem.blogspot.com/2019/06/aem-65-find-duplicate-assets-binaries-in-existing-repository.html)
>* [&#x200B; ontdekt dubbele activa in AEM as a Cloud Service &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/detect-duplicate-assets.html?lang=nl-NL)
