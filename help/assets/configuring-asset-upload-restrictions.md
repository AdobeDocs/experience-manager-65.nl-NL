---
title: Beperkingen voor het uploaden van middelen configureren
description: Beperk het type elementen (bestanden) dat gebruikers kunnen uploaden
contentOwner: AG
role: Developer, Admin, Architect
feature: Asset Management,Upload
exl-id: 0e009b9a-54c4-4715-98ee-0207839f90f6
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 29%

---

# Beperkingen voor het uploaden van middelen configureren {#configuring-asset-upload-restrictions}

U kunt [!DNL Adobe Experience Manager Assets] om het type elementen te beperken dat gebruikers kunnen uploaden. Zo voorkomt u ongewenste uploads in de gewenste indeling en schadelijke bestanden. De `Day CQ DAM Asset Upload Restriction` Met deze service kunt u bepalen welk type bestanden gebruikers kunnen uploaden. Standaard, [!DNL Assets] Hiermee kunnen gebruikers elementen van alle MIME-typen uploaden. U kunt de service echter zo configureren dat gebruikers alleen bestanden van bepaalde MIME-typen kunnen uploaden.

1. Open de Webconsole van de Manager van de Configuratie. Toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Day CQ DAM Asset Upload Restriction]** in de modus Bewerken. Standaard worden de **Alle MIME toestaan** is geselecteerd, zodat gebruikers bestanden van alle MIME-typen kunnen uploaden.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Als u gebruikers wilt beperken zodat zij alleen bestanden van bepaalde MIME-typen kunnen uploaden, schakelt u de optie **[!UICONTROL Allow all MIME]** uit en geeft u toegestane MIME-typen op in de velden **[!UICONTROL Allowed Asset MIMEs (regex)]** met behulp van reguliere expressies.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klikken **[!UICONTROL Save]** om de wijzigingen op te slaan Als u MIME-tekenreeksen opgeeft voor toegestane MIME-typen, mislukt de uploadbewerking voor elke asset met MIME-type dat niet overeenkomt met de geconfigureerde MIME-tekenreeksen in deze velden.
