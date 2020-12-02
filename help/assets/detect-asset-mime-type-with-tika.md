---
title: MIME-type van activa detecteren met Apache Tika
description: Schakel Apache Tika in om te helpen [!DNL Experience Manager Assets] het MIME-type van elementen van de inhoudsstroom te detecteren tijdens het uploaden in plaats van de bestandsextensie.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# MIME-type van elementen detecteren met [!DNL Apache Tika] {#detecting-mime-type-of-assets-using-apache-tika}

Normaliter detecteert [!DNL Adobe Experience Manager Assets] het MIME-type van elementen die u uploadt vanuit de bestandsextensie.

Als u [!DNL Apache Tika] gebruikt om elementen te uploaden, detecteert [!DNL Assets] het MIME-type van de inhoudsstroom tijdens het uploaden in plaats van de bestandsextensie.

Deze functie is standaard uitgeschakeld. Om de eigenschap toe te laten, vorm de **[!UICONTROL Day CQ DAM Mime Type]** dienst van [!UICONTROL Configuration Manager].

>[!NOTE]
>
>MIME-typedetectie met behulp van de [!DNL Apache Tika]-bibliotheek is een resource-intensieve bewerking.

1. Om de Webconsole van de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.

1. Zoek in de lijst met services **[!UICONTROL Day CQ DAM Mime Type Service]** en klik op **[!UICONTROL Edit]**.

1. Selecteer de optie **[!UICONTROL Detect MIME from content]** om het parseren van geüploade elementen in te schakelen om het MIME-type te bepalen terwijl bestandsextensies worden genegeerd. Deze optie is standaard uitgeschakeld.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Klik **[!UICONTROL Save]** om de veranderingen te bewaren.
