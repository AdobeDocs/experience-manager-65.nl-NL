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


# Beperkingen voor het uploaden van elementen {#configuring-asset-upload-restrictions} configureren

U kunt [!DNL Adobe Experience Manager Assets] zodanig configureren dat het type elementen dat gebruikers kunnen uploaden, wordt beperkt. Zo voorkomt u ongewenste uploads in de gewenste indeling en schadelijke bestanden. Met de service `Day CQ DAM Asset Upload Restriction` kunt u bepalen welk type bestanden gebruikers kunnen uploaden. Standaard kunnen gebruikers met [!DNL Assets] elementen van alle MIME-typen uploaden. U kunt de service echter zo configureren dat gebruikers alleen bestanden van bepaalde MIME-typen kunnen uploaden.

1. Open de Webconsole van de Manager van de Configuratie. Ga naar `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de service **[!UICONTROL Day CQ DAM Asset Upload Restriction]** in de modus Bewerken. Standaard is de optie **Alle MIME** toestaan geselecteerd, waarmee gebruikers bestanden van alle MIME-typen kunnen uploaden.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Als u gebruikers wilt beperken zodat zij alleen bestanden van bepaalde MIME-typen kunnen uploaden, schakelt u de optie **[!UICONTROL Allow all MIME]** uit en geeft u toegestane MIME-typen op in de velden **[!UICONTROL Allowed Asset MIMEs (regex)]** met behulp van reguliere expressies.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klik **[!UICONTROL Save]** om de veranderingen te bewaren. Als u MIME-tekenreeksen opgeeft voor toegestane MIME-typen, mislukt de uploadbewerking voor elke asset met MIME-type dat niet overeenkomt met de geconfigureerde MIME-tekenreeksen in deze velden.
