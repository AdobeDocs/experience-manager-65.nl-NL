---
title: Voeg een watermerk toe aan uw digitale elementen.
description: Leer hoe u met de functie Watermerken een digitaal watermerk aan elementen kunt toevoegen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Watermerk uw digitale elementen {#watermarking}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u een digitaal watermerk toevoegen aan elementen waarmee gebruikers de authenticiteit en het auteursrecht van de elementen kunnen controleren. [!DNL Experience Manager Assets] ondersteunt tekst die als watermerk moet worden gebruikt in PNG- en JPEG-bestanden.

Als u een watermerk op elementen wilt toepassen, voegt u de stap Watermerken toe in de workflow [!UICONTROL DAM-element] bijwerken.

1. Open de [!DNL Experience Manager] gebruikersinterface en ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modellen]**.
1. Selecteer op de pagina **[!UICONTROL Workflowmodellen]** de workflow **[!UICONTROL DAM Update Asset]** en klik op **[!UICONTROL Bewerken]**.

1. Sleep vanuit het zijpaneel de stap Watermerk **** toevoegen naar de workflow [!UICONTROL DAM-element] bijwerken.

   ![Sleep de stap Watermerk  toevoegen en voeg deze toe aan de [!UICONTROL DAM Update Asset] workflow](assets/add_watermark_step_aem_assets.png)2
   *Afbeelding: Sleep de stap Watermerktoevoegen en voeg toe aan de workflow[!UICONTROL DAM-element]bijwerken.*

   >[!NOTE]
   >
   >Plaats de stap Watermerk  toevoegen ergens vóór de stap [!UICONTROL Miniatuur] verwerken.

1. Open de stap Watermerk **** toevoegen om de eigenschappen ervan weer te geven.
1. Geef op het tabblad **[!UICONTROL Argumenten]** geldige waarden op in de verschillende velden, zoals tekst, lettertype, grootte, kleur, positie, oriëntatie, enzovoort. Klik op **[!UICONTROL Gereed]** om de wijzigingen te bevestigen.

   ![Geef de argumenten op in de stap Watermerk toevoegen in Elementen](assets/arguments_add_watermark_aem_assets.png)

   *Afbeelding: Geef de argumenten op in de stap Watermerk toevoegen in[!DNL Assets].*

1. Sla de workflow **[!UICONTROL DAM Update Asset]** op met het watermerk.
1. Upload vanuit de [!DNL Assets] gebruikersinterface een voorbeeldelement. Het watermerk wordt weergegeven met de tekengrootte, de kleur enzovoort, op de positie die u in de bovenstaande stappen hebt geconfigureerd.
