---
title: Voeg een watermerk toe aan uw digitale elementen.
description: Leer hoe u met de functie Watermerken een digitaal watermerk aan elementen kunt toevoegen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# Watermerk uw digitale elementen {#watermarking}

Met Adobe Experience Manager (AEM) kunt u een digitaal watermerk toevoegen aan elementen waarmee gebruikers de authenticiteit en het auteursrecht van de elementen kunnen verifiëren. AEM-elementen ondersteunen tekst die als watermerk moet worden gebruikt in PNG- en JPEG-bestanden.

Als u een watermerk op elementen wilt toepassen, voegt u de stap Watermerken toe in de workflow [!UICONTROL DAM-element] bijwerken.

1. Open de AEM-gebruikersinterface en ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Workflow]** > **[!UICONTROL Modellen]**.
1. Selecteer op de pagina **[!UICONTROL Workflowmodellen]** de workflow **[!UICONTROL DAM Update Asset]** en klik op **[!UICONTROL Bewerken]**.

1. Sleep vanuit het zijpaneel de stap Watermerk **** toevoegen naar de workflow [!UICONTROL DAM-element] bijwerken.

   ![Sleep de stap Watermerk  toevoegen en voeg deze toe aan de [!UICONTROL DAM-update-asset] workflow](assets/add_watermark_step_aem_assets.png)2
   *Afbeelding: Sleep de stap Watermerktoevoegen en voeg deze toe aan de workflow voor[!UICONTROL DAM-updatebestanden].*

   >[!NOTE]
   >
   >Plaats de stap Watermerk  toevoegen ergens vóór de stap [!UICONTROL Miniatuur] verwerken.

1. Open de stap Watermerk **** toevoegen om de eigenschappen ervan weer te geven.
1. Geef op het tabblad **[!UICONTROL Argumenten]** geldige waarden op in de verschillende velden, zoals tekst, lettertype, grootte, kleur, positie, oriëntatie, enzovoort. Tik op het pictogram Gereed om de wijzigingen te bevestigen.

   ![Geef de argumenten op in de stap Watermerk toevoegen in Elementen](assets/arguments_add_watermark_aem_assets.png)

   *Afbeelding: Geef de argumenten op in de stap Watermerk toevoegen in Elementen*

1. Sla de workflow **[!UICONTROL DAM Update Asset]** op met het watermerk.
1. Upload een voorbeeldelement vanuit de gebruikersinterface Elementen. Het watermerk wordt weergegeven met de tekengrootte, de kleur enzovoort, op de positie die u in de bovenstaande stappen hebt geconfigureerd.
