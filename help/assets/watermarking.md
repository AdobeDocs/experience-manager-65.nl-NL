---
title: Watermerk toevoegen aan uw digitale elementen
description: Leer hoe u met de functie Watermerken een digitaal watermerk aan elementen kunt toevoegen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5069c2cd26e84866d72a61d36de085dadd556cdd
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# Watermerk op uw digitale elementen {#watermarking}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u een digitaal watermerk toevoegen aan elementen waarmee gebruikers de authenticiteit en het auteursrecht van de elementen kunnen controleren. [!DNL Experience Manager Assets] ondersteunt tekst die als watermerk moet worden gebruikt in PNG- en JPEG-bestanden.

Als u een watermerk op elementen wilt toepassen, voegt u de stap Watermerken toe in de [!UICONTROL DAM Update Asset]-workflow.

1. Open de [!DNL Experience Manager] gebruikersinterface en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** de **[!UICONTROL DAM Update Asset]**-workflow en klik op **[!UICONTROL Edit]**.

1. Sleep vanuit het zijpaneel de stap **[!UICONTROL Add Watermark]** naar de [!UICONTROL DAM Update Asset]-workflow.

   ![Sleep de  [!UICONTROL Add Watermark] stap en voeg deze toe aan de  [!UICONTROL DAM Update Asset] workflow](assets/add_watermark_step_aem_assets.png)
 2
   *Afbeelding: Sleep de  [!UICONTROL Add Watermark] stap en voeg deze toe aan de  [!UICONTROL DAM Update Asset] workflow.*

   >[!NOTE]
   >
   >Plaats de [!UICONTROL Add Watermark] stap ergens vóór de [!UICONTROL Process Thumbnail] stap.

1. Open de stap **[!UICONTROL Add Watermark]** om de eigenschappen ervan weer te geven.
1. Geef op het tabblad **[!UICONTROL Arguments]** geldige waarden op in de verschillende velden, zoals tekst, lettertype, grootte, kleur, positie, oriëntatie, enzovoort. Klik op **[!UICONTROL Done]** om de wijzigingen te bevestigen.

   ![Geef de argumenten op in de stap Watermerk toevoegen in Elementen](assets/arguments_add_watermark_aem_assets.png)

   *Afbeelding: Geef de argumenten op in de stap Watermerk toevoegen in  [!DNL Assets].*

1. Sla de **[!UICONTROL DAM Update Asset]**-workflow op met de watermerkstap.
1. Upload een voorbeeldelement vanuit de gebruikersinterface [!DNL Assets]. Het watermerk wordt weergegeven met de tekengrootte, de kleur enzovoort, op de positie die u in de bovenstaande stappen hebt geconfigureerd.

Als u PDF-documenten programmatisch of met dynamische informatie wilt voorzien van een watermerk, kunt u [Document Services](/help/forms/using/overview-aem-document-services.md) Experience Managers gebruiken.
