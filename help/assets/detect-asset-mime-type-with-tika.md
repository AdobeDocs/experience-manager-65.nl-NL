---
title: MIME-type van activa detecteren met Apache Tika
description: Laat Tika Apache toe helpen  [!DNL Experience Manager Assets]  het MIME type van activa van de inhoudsstroom tijdens uploadt verrichting in plaats van de dossieruitbreiding ontdekken.
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

Normaal gesproken detecteert [!DNL Adobe Experience Manager Assets] het MIME-type van elementen die u uploadt vanuit de bestandsextensie.

Als u [!DNL Apache Tika] gebruikt om elementen te uploaden, detecteert [!DNL Assets] het MIME-type van de inhoudsstroom tijdens het uploaden in plaats van de bestandsextensie.

Deze functie is standaard uitgeschakeld. Als u deze functie wilt inschakelen, configureert u de service **[!UICONTROL Day CQ DAM Mime Type]** vanuit [!UICONTROL Configuration Manager] .

>[!NOTE]
>
>MIME-typedetectie met behulp van de [!DNL Apache Tika] -bibliotheek is een resource-intensieve bewerking.

1. Om de Webconsole van de Manager van de Configuratie te openen, toegang `https://[aem_server]:[port]/system/console/configMgr`.

1. Zoek **[!UICONTROL Day CQ DAM Mime Type Service]** in de lijst met services en klik op **[!UICONTROL Edit]** .

1. Selecteer de optie **[!UICONTROL Detect MIME from content]** om het parseren van geüploade elementen in te schakelen om het MIME-type te bepalen terwijl bestandsextensies worden genegeerd. Deze optie is standaard uitgeschakeld.

   ![&#x200B; chlimage_1-333 &#x200B;](assets/chlimage_1-333.png)

1. Klik op **[!UICONTROL Save]** om de wijzigingen op te slaan.
