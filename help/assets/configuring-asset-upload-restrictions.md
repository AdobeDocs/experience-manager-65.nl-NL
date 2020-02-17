---
title: Beperkingen voor het uploaden van middelen configureren
description: 'Beperk het type elementen (bestanden) dat gebruikers kunnen uploaden '
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Beperkingen voor het uploaden van middelen configureren {#configuring-asset-upload-restrictions}

U kunt Adobe Experience Manager (AEM)-middelen configureren om het type elementen (bestanden) te beperken dat gebruikers kunnen uploaden. Met deze functie voorkomt u dat gebruikers elementen in een ongewenste indeling kunnen uploaden of schadelijke bestanden kunnen uploaden. Met de `Day CQ DAM Asset Upload Restriction` service kunt u bepalen welk type bestanden gebruikers kunnen uploaden. Standaard kunnen gebruikers met AEM-middelen elementen van alle MIME-typen uploaden. U kunt de service echter zo configureren dat gebruikers alleen bestanden van bepaalde MIME-typen kunnen uploaden.

1. Open de Webconsole van de Manager van de Configuratie. Toegang `https://[aem_server]:[port]/system/console/configMgr`.
1. Open de **[!UICONTROL Day CQ DAM Asset Upload Restriction]** Service in de bewerkingsmodus. Standaard is de optie **Alle MIME** toestaan ingeschakeld, waarmee gebruikers bestanden van alle MIME-typen kunnen uploaden.

   ![chlimage_1-378](assets/chlimage_1-378.png)

1. Als u gebruikers alleen wilt beperken bij het uploaden van bestanden van bepaalde MIME-typen, schakelt u de optie **[!UICONTROL Alle MIME]** toestaan uit en geeft u toegestane MIME-typen op in de velden MIME&#39;s **[!UICONTROL toegestane elementen (regex)]** met behulp van reguliere expressies.

   ![chlimage_1-379](assets/chlimage_1-379.png)

1. Klik op **[!UICONTROL Opslaan]** of tik op Opslaan om de wijzigingen op te slaan. Als u MIME-tekenreeksen opgeeft voor toegestane MIME-typen, mislukt de uploadbewerking voor elk element met MIME-type dat niet overeenkomt met de geconfigureerde MIME-tekenreeksen in deze velden.
