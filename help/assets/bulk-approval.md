---
title: Mapelementen en -verzamelingen controleren
description: Stel revisieworkflows in voor elementen in een map of verzameling en deel deze met revisoren of creatieve partners om feedback te zoeken.
contentOwner: AG
feature: Collaboration, Collections
role: User
exl-id: 23c90e10-aa03-450e-9fb0-2f5be0c5066b
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 4%

---

# Mapelementen en -verzamelingen controleren {#review-folder-assets-and-collections}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/bulk-approval.html?lang=en) |
| AEM 6,5 | Dit artikel |

Stel revisieworkflows in voor elementen in een map of verzameling en deel deze met revisoren of creatieve partners om feedback te zoeken.

[!DNL Adobe Experience Manager Assets] Hiermee kunt u een workflow voor ad-hocrevisies instellen voor elementen in een map of verzameling en deze delen met revisoren of creatieve partners om feedback te zoeken.

U kunt de revisiewerkstroom aan een project koppelen of een onafhankelijke revisietaak maken.

Nadat u de middelen hebt gedeeld, kunnen revisoren deze goedkeuren of afwijzen. Meldingen worden in verschillende fasen van de workflow verzonden om beoogde ontvangers op de hoogte te stellen van de voltooiing van verschillende taken. Als u bijvoorbeeld een map of verzameling deelt, ontvangt de controleur een melding dat een map of verzameling is gedeeld voor revisie.

Nadat de controleur de revisie heeft voltooid (activa goedkeurt of verwerpt), ontvangt u een bericht dat de revisie is voltooid.

## Een revisietaak voor mappen maken {#creating-a-review-task-for-folders}

1. Van de [!DNL Assets] -gebruikersinterface, selecteert u de map waarvoor u een revisietaak wilt maken.
1. Klik op de werkbalk op **[!UICONTROL Create Review Task]** ![revisietaak maken](assets/do-not-localize/create-review-task.png) om de **[!UICONTROL Review Task]** pagina. Als de optie niet wordt weergegeven op de werkbalk, klikt u op **[!UICONTROL More]** en selecteert u vervolgens de optie.

1. (Optioneel) Van de **[!UICONTROL Project]** selecteert u het project waaraan u de revisietaak wilt koppelen. Standaard worden de **[!UICONTROL None]** is geselecteerd. Als u geen project aan de overzichtstaak wilt associëren, behoud deze selectie.

   >[!NOTE]
   >
   >Slechts zijn de projecten waarvoor u de (of hogere) toestemmingen op het niveau van de Redacteur hebt zichtbaar in **[!UICONTROL Projects]** lijst.

1. Voer een naam in voor de revisietaak en selecteer een fiatteur in het menu **[!UICONTROL Assign To]** lijst.

   >[!NOTE]
   >
   >De leden/groepen van het geselecteerde project zijn beschikbaar als fiatteurs in **[!UICONTROL Assign To]** lijst.

1. Voer een beschrijving, de prioriteit van de taak en de vervaldatum voor de controletaak in.

   ![task_details](assets/task_details.png)

1. Voer op het tabblad Geavanceerd een label in dat u wilt gebruiken om de URI te maken.

   ![review_name](assets/review_name.png)

1. Klikken **[!UICONTROL Submit]** en klik vervolgens op **[!UICONTROL Done]** om het bevestigingsbericht te sluiten. Er wordt een bericht voor de nieuwe taak naar de goedkeurder verzonden.
1. Aanmelden bij [!DNL Assets] als fiatteur en navigeer naar de [!DNL Assets] UI. Klik op **[!UICONTROL Notifications]** en selecteer vervolgens de revisietaak in de lijst.

   ![Melding van activa](assets/aemAssetsNotification.png)

1. In de **[!UICONTROL Review Task]** pagina, onderzoekt u de details van de revisietaak en klikt u vervolgens op **[!UICONTROL Review]**.
1. In de **[!UICONTROL Review Task]** pagina, selecteer elementen en klik op **[!UICONTROL Approve/Reject]** in voorkomend geval goed te keuren of af te wijzen.

   ![review_task](assets/review_task.png)

1. Klik op **[!UICONTROL Complete]** op de werkbalk. Voer in het dialoogvenster een opmerking in en klik op  **[!UICONTROL Complete]** ter bevestiging.
1. Ga naar de [!DNL Assets] en opent u de map. De pictogrammen voor de goedkeuringsstatus van de elementen worden weergegeven in de kaartweergave en de lijstweergave.

   **Kaartweergave**

   ![Status controleren zoals deze wordt weergegeven in de kaartweergave](assets/chlimage_1-404.png)

   **Lijstweergave**

   ![Status controleren zoals deze wordt weergegeven in de lijstweergave](assets/review_status_listview.png)

## Een revisietaak voor verzamelingen maken {#creating-a-review-task-for-collections}

1. Selecteer op de pagina Verzamelingen de verzameling waarvoor u een revisietaak wilt maken.
1. Klik op de werkbalk op **[!UICONTROL Create Review Task]** ![revisietaak maken](assets/do-not-localize/create-review-task.png) om de **[!UICONTROL Review Task]** pagina. Als de optie niet wordt weergegeven op de werkbalk, klikt u op **[!UICONTROL More]** en selecteert u vervolgens de optie.

1. (Optioneel) Van de **[!UICONTROL Project]** selecteert u het project waaraan u de revisietaak wilt koppelen. Standaard worden de **[!UICONTROL None]** is geselecteerd. Als u geen project aan de overzichtstaak wilt associëren, behoud deze selectie.

   >[!NOTE]
   >
   >Slechts zijn de projecten waarvoor u de (of hogere) toestemmingen op het niveau van de Redacteur hebt zichtbaar in **[!UICONTROL Projects]** lijst.

1. Voer een naam in voor de revisietaak en selecteer een fiatteur in het menu **[!UICONTROL Assign To]** lijst.

   >[!NOTE]
   >
   >De leden/groepen van het geselecteerde project zijn beschikbaar als fiatteurs in **[!UICONTROL Assign To]** lijst.

1. Voer een beschrijving, de prioriteit van de taak en de vervaldatum voor de controletaak in.

   ![task_details-collection](assets/task_details-collection.png)

1. Klikken **[!UICONTROL Submit]** en klik vervolgens op **[!UICONTROL Done]** om het bevestigingsbericht te sluiten. Er wordt een bericht voor de nieuwe taak naar de goedkeurder verzonden.
1. Aanmelden bij [!DNL Assets] als fiatteur en navigeer naar de [!DNL Assets] console. Klik op **[!UICONTROL Notifications]** en selecteer vervolgens de revisietaak in de lijst.
1. In de **[!UICONTROL Review Task]** pagina, onderzoekt u de details van de revisietaak en klikt u vervolgens op **[!UICONTROL Review]**.
1. Alle elementen in de verzameling zijn zichtbaar op de controlepagina. Selecteer de elementen en klik op **[!UICONTROL Approve/Reject]** activa goedkeuren of afwijzen, al naargelang het geval.

   ![review_task_collection](assets/review_task_collection.png)

1. Klik op **[!UICONTROL Complete]** op de werkbalk. Voer in het dialoogvenster een opmerking in en klik op **[!UICONTROL Complete]** ter bevestiging.
1. Navigeer naar de verzamelingsconsole en open de verzameling. De pictogrammen voor de goedkeuringsstatus van de elementen worden weergegeven in zowel de Kaart- als lijstweergave.

   ![collection_reviewStatusCard, weergave](assets/collection_reviewstatuscardview.png)

   *Afbeelding: Kaartweergave.*

   ![collection_reviewstatus listview](assets/collection_reviewstatuslistview.png)

   *Afbeelding: Lijstweergave.*
