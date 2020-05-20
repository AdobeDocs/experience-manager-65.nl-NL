---
title: Beperkingen voor het uploaden van middelen configureren
description: 'Beperk het type elementen (bestanden) dat gebruikers kunnen uploaden '
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 30%

---


# Beperkingen voor het uploaden van middelen configureren {#configuring-asset-upload-restrictions}

U kunt configureren [!DNL Adobe Experience Manager Assets] om het type elementen te beperken dat gebruikers kunnen uploaden. Zo voorkomt u ongewenste uploads in de gewenste indeling en schadelijke bestanden. Met de `Day CQ DAM Asset Upload Restriction` service kunt u bepalen welk type bestanden gebruikers kunnen uploaden. Standaard [!DNL Assets] kunnen gebruikers elementen van alle MIME-typen uploaden. U kunt de service echter zo configureren dat gebruikers alleen bestanden van bepaalde MIME-typen kunnen uploaden.

1. Open de Webconsole van de Manager van de Configuratie. Ga naar `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Day CQ DAM Asset Upload Restriction]** service in Edit mode. Standaard is de optie **Alle MIME** toestaan geselecteerd, waarmee gebruikers bestanden van alle MIME-typen kunnen uploaden.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Als u gebruikers wilt beperken zodat zij alleen bestanden van bepaalde MIME-typen kunnen uploaden, schakelt u de optie **[!UICONTROL Allow all MIME]** uit en geeft u toegestane MIME-typen op in de velden **[!UICONTROL Allowed Asset MIMEs (regex)]** met behulp van reguliere expressies.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Click **[!UICONTROL Save]** to save the changes. Als u MIME-tekenreeksen opgeeft voor toegestane MIME-typen, mislukt de uploadbewerking voor elke asset met MIME-type dat niet overeenkomt met de geconfigureerde MIME-tekenreeksen in deze velden.
