---
title: Watermerk toevoegen aan uw digitale elementen
description: Leer hoe u met de functie Watermerken een digitaal watermerk aan elementen kunt toevoegen.
contentOwner: AG
role: User, Admin
feature: Asset Management
exl-id: bc0cfb0e-3f70-4377-8831-326a7cae73bd
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 1%

---

# Watermerk uw digitale elementen {#watermarking}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/watermark-assets.html?lang=en) |
| AEM 6,5 | Dit artikel |

[!DNL Adobe Experience Manager Assets] Hiermee kunt u een digitaal watermerk toevoegen aan elementen waarmee gebruikers de authenticiteit en de copyrighteigendom van de elementen kunnen verifiëren. [!DNL Experience Manager Assets] ondersteunt tekst die als watermerk moet worden gebruikt op PNG- en JPEG-bestanden.

Als u een watermerk wilt toepassen op elementen, voegt u de stap Watermerken toe in het dialoogvenster [!UICONTROL DAM Update Asset] workflow.

1. Toegang krijgen tot de [!DNL Experience Manager] gebruikersinterface en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
1. Van de **[!UICONTROL Workflow Models]** pagina, selecteert u de **[!UICONTROL DAM Update Asset]** workflow en klik op **[!UICONTROL Edit]**.

1. Sleep vanuit het zijpaneel de **[!UICONTROL Add Watermark]** stap naar de [!UICONTROL DAM Update Asset] workflow.

   ![Sleep de [!UICONTROL Add Watermark] en toevoegen aan de [!UICONTROL DAM Update Asset] werkstroom](assets/add_watermark_step_aem_assets.png)

   *Figuur: Sleep de [!UICONTROL Add Watermark] en toevoegen aan de [!UICONTROL DAM Update Asset] workflow.*

   >[!NOTE]
   >
   >Plaats de [!UICONTROL Add Watermark] stap overal vóór de [!UICONTROL Process Thumbnail] stap.

1. Open de **[!UICONTROL Add Watermark]** stap om de eigenschappen weer te geven.
1. In de **[!UICONTROL Arguments]** op in de verschillende velden geldige waarden, zoals tekst, lettertype, grootte, kleur, positie, richting enzovoort. Klik op **[!UICONTROL Done]**.

   ![Geef de argumenten op in de stap Watermerk toevoegen in [!DNL Assets]](assets/arguments_add_watermark_aem_assets.png)

   *Afbeelding: geef de argumenten op in de stap Watermerk toevoegen in [!DNL Assets].*

1. Sla de **[!UICONTROL DAM Update Asset]** workflow met het watermerk.
1. Van de [!DNL Assets] -gebruikersinterface, uploadt u een voorbeeldelement. Het watermerk wordt weergegeven met de tekengrootte, kleur, enzovoort, op de positie die u in de bovenstaande stappen hebt geconfigureerd.

Als u PDF-documenten met watermerk programmatisch of met dynamische informatie wilt gebruiken, kunt u [Experience Manager Document Services](/help/forms/using/overview-aem-document-services.md) aanbieden.

## Tips en beperkingen {#tips-limitations}

* Alleen op tekst gebaseerde watermerken worden ondersteund. Afbeeldingen worden niet gebruikt als watermerken, ook al kunt u afbeeldingen uploaden wanneer u de [!UICONTROL Add Watermark Process].
* Alleen PNG- en JPEG-bestanden worden ondersteund voor een watermerk. Andere indelingen van elementen zijn niet van een watermerk voorzien.
