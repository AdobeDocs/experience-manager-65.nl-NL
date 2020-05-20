---
title: MIME-type van activa detecteren met Apache Tika
description: Schakel Apache Tika in om AEM Assets te helpen het MIME-type van elementen van de inhoudsstroom te detecteren tijdens het uploaden in plaats van de bestandsextensie.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# MIME-type van activa detecteren met Apache Tika {#detecting-mime-type-of-assets-using-apache-tika}

Normaliter wordt in Adobe Experience Manager (AEM) het MIME-type van middelen gedetecteerd dat u uploadt vanuit de bestandsextensie.

Als u Apache Tika gebruikt om activa te uploaden, ontdekt AEM Middelen hun MIME type van de inhoudsstroom tijdens het uploaden verrichting in plaats van de dossieruitbreiding.

Deze functie is standaard uitgeschakeld. Om de eigenschap toe te laten, vorm de **[!UICONTROL Day CQ DAM Mime Type]** dienst van [!UICONTROL Configuration Manager].

>[!NOTE]
>
>MIME-typedetectie met behulp van de Apache Tika-bibliotheek is een hulpbronnenintensieve bewerking.

1. Om de Webconsole van de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.

1. Zoek in de lijst met services **[!UICONTROL Day CQ DAM Mime Type Service]** en klik op **[!UICONTROL Edit]**.

1. Selecteer de **[!UICONTROL Detect MIME from content]** optie om het parseren van geüploade elementen in te schakelen om het MIME-type te bepalen terwijl bestandsextensies worden genegeerd. Deze optie is standaard uitgeschakeld.

   ![chlimage_1-333](assets/chlimage_1-333.png)

1. Click **[!UICONTROL Save]** to save the changes.
