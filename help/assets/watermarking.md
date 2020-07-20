---
title: Voeg een watermerk toe aan uw digitale elementen.
description: Leer hoe u met de functie Watermerken een digitaal watermerk aan elementen kunt toevoegen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5035d3457187f4d5fe5c2af255a1a886df7291b4
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Watermerk uw digitale elementen {#watermarking}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u een digitaal watermerk toevoegen aan elementen waarmee gebruikers de authenticiteit en het auteursrecht van de elementen kunnen controleren. [!DNL Experience Manager Assets] ondersteunt tekst die als watermerk moet worden gebruikt in PNG- en JPEG-bestanden.

Als u een watermerk op elementen wilt toepassen, voegt u de stap Watermerken toe aan de [!UICONTROL DAM Update Asset] workflow.

1. Open de [!DNL Experience Manager] gebruikersinterface en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Selecteer de **[!UICONTROL Workflow Models]** workflow op de **[!UICONTROL DAM Update Asset]** pagina en klik op **[!UICONTROL Edit]**.

1. Sleep de **[!UICONTROL Add Watermark]** stap vanuit het zijpaneel naar de [!UICONTROL DAM Update Asset] workflow.

   ![Sleep de [!UICONTROL Add Watermark] stap en voeg deze toe aan de [!UICONTROL DAM Update Asset] workflow](assets/add_watermark_step_aem_assets.png)2
   *Afbeelding: Sleep de[!UICONTROL Add Watermark]stap en voeg deze toe aan de[!UICONTROL DAM Update Asset]workflow.*

   >[!NOTE]
   >
   >Plaats de [!UICONTROL Add Watermark] stap ergens voor de [!UICONTROL Process Thumbnail] stap.

1. Open de **[!UICONTROL Add Watermark]** stap om de eigenschappen ervan weer te geven.
1. Geef op het **[!UICONTROL Arguments]** tabblad geldige waarden op in de verschillende velden, zoals tekst, lettertype, grootte, kleur, positie, richting enzovoort. Klik op **[!UICONTROL Done]** om de wijzigingen te bevestigen.

   ![Geef de argumenten op in de stap Watermerk toevoegen in Elementen](assets/arguments_add_watermark_aem_assets.png)

   *Afbeelding: Geef de argumenten op in de stap Watermerk toevoegen in[!DNL Assets].*

1. Save the **[!UICONTROL DAM Update Asset]** workflow with the watermark step.
1. Upload vanuit de [!DNL Assets] gebruikersinterface een voorbeeldelement. Het watermerk wordt weergegeven met de tekengrootte, de kleur enzovoort, op de positie die u in de bovenstaande stappen hebt geconfigureerd.

Als u PDF-documenten programmatisch of met dynamische informatie wilt voorzien van een watermerk, kunt u het [aanbod van AEM Document Services](/help/forms/using/overview-aem-document-services.md) gebruiken.
