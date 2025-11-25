---
title: Beperkingen voor het uploaden van middelen configureren
description: Beperk het type elementen (bestanden) dat gebruikers kunnen uploaden
contentOwner: AG
role: Developer, Admin
feature: Asset Management,Upload
exl-id: 0e009b9a-54c4-4715-98ee-0207839f90f6
solution: Experience Manager, Experience Manager Assets
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 14%

---

# Beperkingen voor het uploaden van middelen configureren {#configuring-asset-upload-restrictions}

U kunt [!DNL Adobe Experience Manager Assets] zo configureren dat het type elementen dat gebruikers kunnen uploaden, wordt beperkt. Zo voorkomt u ongewenste uploads in de gewenste indeling en schadelijke bestanden. Met de service `Day CQ DAM Asset Upload Restriction` kunt u bepalen welk type bestanden gebruikers kunnen uploaden. In [!DNL Assets] kunnen gebruikers standaard elementen van alle MIME-typen uploaden. U kunt de service echter zo configureren dat gebruikers alleen bestanden van bepaalde MIME-typen kunnen uploaden.

1. Open de Webconsole van de Manager van de Configuratie. Toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de service **[!UICONTROL Day CQ DAM Asset Upload Restriction]** in de modus Bewerken. Door gebrek, **staat al MIME** optie toe wordt geselecteerd, die gebruikers toestaat om dossiers van alle types te uploaden MIME.

   ![&#x200B; chlimage_1-378 &#x200B;](assets/chlimage_1-378.png)

1. Als u gebruikers wilt beperken zodat zij alleen bestanden van bepaalde MIME-typen kunnen uploaden, schakelt u de optie **[!UICONTROL Allow all MIME]** uit en geeft u toegestane MIME-typen op in de velden **[!UICONTROL Allowed Asset MIMEs (regex)]** met behulp van reguliere expressies.

   ![&#x200B; chlimage_1-379 &#x200B;](assets/chlimage_1-379.png)

1. Klik op **[!UICONTROL Save]** om de wijzigingen op te slaan. Als u MIME-tekenreeksen opgeeft voor toegestane MIME-typen, mislukt de uploadbewerking voor elk element met MIME-type dat niet overeenkomt met de geconfigureerde MIME-tekenreeksen in deze velden.
