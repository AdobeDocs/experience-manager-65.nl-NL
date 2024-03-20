---
title: MIME-type van activa detecteren met Apache Tika
description: Apache Tika inschakelen om te helpen [!DNL Experience Manager Assets] detecteer het MIME-type van elementen van de inhoudsstroom tijdens het uploaden in plaats van de bestandsextensie.
contentOwner: AG
role: Admin, Architect
feature: Metadata,Developer Tools,Asset Management
exl-id: a312466d-8d84-4c94-af85-1549afc61aed
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# MIME-type van elementen detecteren met [!DNL Apache Tika] {#detecting-mime-type-of-assets-using-apache-tika}

Normaal gesproken, [!DNL Adobe Experience Manager Assets] detecteert het MIME-type elementen dat u uploadt vanuit de bestandsextensie.

Als u [!DNL Apache Tika] om elementen te uploaden, [!DNL Assets] detecteert het MIME-type van de inhoud tijdens het uploaden in plaats van de bestandsextensie.

Deze functie is standaard uitgeschakeld. Om de eigenschap toe te laten, vorm **[!UICONTROL Day CQ DAM Mime Type]** service van [!UICONTROL Configuration Manager].

>[!NOTE]
>
>MIME-typedetectie met behulp van [!DNL Apache Tika] bibliotheek is een hulpbronnenintensieve bewerking.

1. Om de Webconsole van de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.

1. Van de lijst van de diensten, bepaal **[!UICONTROL Day CQ DAM Mime Type Service]** en klik op **[!UICONTROL Edit]**.

1. Selecteer de **[!UICONTROL Detect MIME from content]** optie om het parseren van geüploade elementen in staat te stellen hun MIME-type te bepalen terwijl bestandsextensies worden genegeerd. Deze optie is standaard uitgeschakeld.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klikken **[!UICONTROL Save]** om de wijzigingen op te slaan
