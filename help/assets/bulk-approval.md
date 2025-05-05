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
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/bulk-approval.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

Stel revisieworkflows in voor elementen in een map of verzameling en deel deze met revisoren of creatieve partners om feedback te zoeken.

Met [!DNL Adobe Experience Manager Assets] kunt u een workflow voor ad-hocrevisies instellen voor elementen in een map of verzameling en deze delen met revisoren of creatieve partners om feedback te zoeken.

U kunt de revisiewerkstroom aan een project koppelen of een onafhankelijke revisietaak maken.

Nadat u de middelen hebt gedeeld, kunnen revisoren deze goedkeuren of afwijzen. Meldingen worden in verschillende fasen van de workflow verzonden om beoogde ontvangers op de hoogte te stellen van de voltooiing van verschillende taken. Als u bijvoorbeeld een map of verzameling deelt, ontvangt de controleur een melding dat een map of verzameling is gedeeld voor revisie.

Nadat de controleur de revisie heeft voltooid (activa goedkeurt of verwerpt), ontvangt u een bericht dat de revisie is voltooid.

## Een revisietaak voor mappen maken {#creating-a-review-task-for-folders}

1. Selecteer in de gebruikersinterface van [!DNL Assets] de map waarvoor u een revisietaak wilt maken.
1. Van de toolbar, klik **[!UICONTROL Create Review Task]** ![ creeer overzichtstaak ](assets/do-not-localize/create-review-task.png) om de **[!UICONTROL Review Task]** pagina te openen. Als de optie niet wordt weergegeven op de werkbalk, klikt u op **[!UICONTROL More]** en selecteert u de optie.

1. (Optioneel) Selecteer in de lijst **[!UICONTROL Project]** het project waaraan u de revisietaak wilt koppelen. Standaard is de optie **[!UICONTROL None]** geselecteerd. Als u geen project aan de overzichtstaak wilt associëren, behoud deze selectie.

   >[!NOTE]
   >
   >Alleen de projecten waarvoor u de machtiging op Editor (of hoger) hebt, zijn zichtbaar in de lijst **[!UICONTROL Projects]** .

1. Voer een naam in voor de revisietaak en selecteer een fiatteur in de lijst **[!UICONTROL Assign To]** .

   >[!NOTE]
   >
   >De leden/groepen van het geselecteerde project zijn beschikbaar als fiatteurs in de **[!UICONTROL Assign To]** lijst.

1. Voer een beschrijving, de prioriteit van de taak en de vervaldatum voor de controletaak in.

   ![ task_details ](assets/task_details.png)

1. Voer op het tabblad Geavanceerd een label in dat u wilt gebruiken om de URI te maken.

   ![ review_name ](assets/review_name.png)

1. Klik op **[!UICONTROL Submit]** en klik vervolgens op **[!UICONTROL Done]** om het bevestigingsbericht te sluiten. Er wordt een bericht voor de nieuwe taak naar de goedkeurder verzonden.
1. Meld u aan bij [!DNL Assets] als fiatteur en ga naar de gebruikersinterface van [!DNL Assets] . Als u elementen wilt goedkeuren, klikt u op **[!UICONTROL Notifications]** en selecteert u de revisietaak in de lijst.

   ![ het bericht van Assets ](assets/aemAssetsNotification.png)

1. Controleer op de pagina **[!UICONTROL Review Task]** de details van de revisietaak en klik vervolgens op **[!UICONTROL Review]** .
1. Selecteer op de pagina **[!UICONTROL Review Task]** elementen en klik op **[!UICONTROL Approve/Reject]** om deze goed te keuren of af te wijzen.

   ![ review_task ](assets/review_task.png)

1. Klik op **[!UICONTROL Complete]** op de werkbalk. Voer in het dialoogvenster een opmerking in en klik op **[!UICONTROL Complete]** om te bevestigen.
1. Navigeer naar de gebruikersinterface van [!DNL Assets] en open de map. De pictogrammen voor de goedkeuringsstatus van de elementen worden weergegeven in de kaartweergave en de lijstweergave.

   **mening van de Kaart**

   ![ status van het Overzicht zoals gezien in kaartmening ](assets/chlimage_1-404.png)

   **mening van de Lijst**

   ![ status van het Overzicht zoals gezien in lijstmening ](assets/review_status_listview.png)

## Een revisietaak voor verzamelingen maken {#creating-a-review-task-for-collections}

1. Selecteer op de pagina Verzamelingen de verzameling waarvoor u een revisietaak wilt maken.
1. Van de toolbar, klik **[!UICONTROL Create Review Task]** ![ creeer overzichtstaak ](assets/do-not-localize/create-review-task.png) om de **[!UICONTROL Review Task]** pagina te openen. Als de optie niet wordt weergegeven op de werkbalk, klikt u op **[!UICONTROL More]** en selecteert u de optie.

1. (Optioneel) Selecteer in de lijst **[!UICONTROL Project]** het project waaraan u de revisietaak wilt koppelen. Standaard is de optie **[!UICONTROL None]** geselecteerd. Als u geen project aan de overzichtstaak wilt associëren, behoud deze selectie.

   >[!NOTE]
   >
   >Alleen de projecten waarvoor u de machtiging op Editor (of hoger) hebt, zijn zichtbaar in de lijst **[!UICONTROL Projects]** .

1. Voer een naam in voor de revisietaak en selecteer een fiatteur in de lijst **[!UICONTROL Assign To]** .

   >[!NOTE]
   >
   >De leden/groepen van het geselecteerde project zijn beschikbaar als fiatteurs in de **[!UICONTROL Assign To]** lijst.

1. Voer een beschrijving, de prioriteit van de taak en de vervaldatum voor de controletaak in.

   ![ task_details-collection ](assets/task_details-collection.png)

1. Klik op **[!UICONTROL Submit]** en klik vervolgens op **[!UICONTROL Done]** om het bevestigingsbericht te sluiten. Er wordt een bericht voor de nieuwe taak naar de goedkeurder verzonden.
1. Meld u aan bij [!DNL Assets] als fiatteur en ga naar de [!DNL Assets] -console. Als u elementen wilt goedkeuren, klikt u op **[!UICONTROL Notifications]** en selecteert u de revisietaak in de lijst.
1. Controleer op de pagina **[!UICONTROL Review Task]** de details van de revisietaak en klik vervolgens op **[!UICONTROL Review]** .
1. Alle elementen in de verzameling zijn zichtbaar op de controlepagina. Selecteer de elementen en klik op **[!UICONTROL Approve/Reject]** om de elementen goed te keuren of af te wijzen.

   ![ review_task_collection ](assets/review_task_collection.png)

1. Klik op **[!UICONTROL Complete]** op de werkbalk. Voer in het dialoogvenster een opmerking in en klik op **[!UICONTROL Complete]** om te bevestigen.
1. Navigeer naar de verzamelingsconsole en open de verzameling. De pictogrammen voor de goedkeuringsstatus van de elementen worden weergegeven in zowel de Kaart- als lijstweergave.

   ![ collection_reviewstatuscardview ](assets/collection_reviewstatuscardview.png)

   *Cijfer: De mening van de Kaart.*

   ![ collection_reviewstatuslistview ](assets/collection_reviewstatuslistview.png)

   *Cijfer: De mening van de Lijst.*
