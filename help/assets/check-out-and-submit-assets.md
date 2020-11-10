---
title: Elementen in- en uitchecken voor bewerking
description: Leer hoe u middelen kunt uitchecken voor bewerking en ze weer kunt inchecken nadat de wijzigingen zijn voltooid.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 12c56c27c7f97f1029c757ec6d28f482516149d0
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---


# Bestanden inchecken en uitchecken in [!DNL Experience Manager] DAM {#check-in-and-check-out-files-in-assets}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u elementen uitchecken voor bewerking en ze weer inchecken nadat u alle wijzigingen hebt aangebracht. Nadat u een element hebt uitgecheckt, kunt u het element alleen bewerken, annoteren, publiceren, verplaatsen of verwijderen. Als u een element uitcheckt, vergrendelt u het element. Andere gebruikers kunnen geen van deze bewerkingen op het element uitvoeren totdat u het element weer incheckt bij [!DNL Assets]. Ze kunnen echter wel de metagegevens van het vergrendelde element wijzigen.

Om activa te kunnen uitchecken/inchecken, hebt u schrijftoegang op hen nodig.

Met deze functie voorkomt u dat andere gebruikers de wijzigingen overschrijven die door een auteur zijn aangebracht en waarbij meerdere gebruikers samenwerken aan het bewerken van workflows in verschillende teams.

## Elementen uitchecken {#checking-out-assets}

1. Selecteer in de [!DNL Assets] gebruikersinterface het element dat u wilt uitchecken. U kunt ook meerdere elementen selecteren om uit te checken.
1. Klik **[!UICONTROL Checkout]** op de werkbalk.
Met de **[!UICONTROL Checkout]** optie schakelt u over naar **[!UICONTROL Checkin]**.
Meld u aan als een andere gebruiker om te controleren of andere gebruikers het uitgecheckte element kunnen bewerken. Er wordt een vergrendelingssymbool weergegeven op de miniatuur van het element dat u hebt uitgecheckt.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   Selecteer het element. Op de werkbalk worden geen opties weergegeven waarmee u elementen kunt bewerken, notities kunt aanbrengen, kunt publiceren of verwijderen.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   U kunt klikken **[!UICONTROL View Properties]** om de metagegevens voor het vergrendelde element te bewerken.

1. Klik **[!UICONTROL Edit]** om het element te openen in de bewerkingsmodus.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. Bewerk het element en sla de wijzigingen op. Snijd bijvoorbeeld de afbeelding bij en sla deze op.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   U kunt er ook voor kiezen om het element te annoteren of te publiceren.

1. Selecteer het bewerkte element in de [!DNL Assets] interface en klik op **[!UICONTROL Checkin]** de werkbalk. Het gewijzigde element is ingecheckt bij [!DNL Assets] en is beschikbaar voor andere gebruikers voor bewerking.

## Geforceerd inchecken {#forced-check-in}

Beheerders kunnen elementen inchecken die door andere gebruikers zijn uitgecheckt.

1. Meld u aan [!DNL Assets] als beheerder.
1. Selecteer in de [!DNL Assets] gebruikersinterface een of meer elementen die door andere gebruikers zijn uitgecheckt.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klik **[!UICONTROL Release Lock]** op de werkbalk. Het element is ingecheckt en kan worden bewerkt aan andere gebruikers.

## Aanbevolen werkwijzen en beperkingen {#tips-limitations}

* Het is mogelijk om een *map* te verwijderen die uitgecheckte elementbestanden bevat. Voordat u een map verwijdert, moet u controleren of er geen digitale elementen zijn uitgecheckt door gebruikers.

>[!MORELIKETHIS]
>
>* [Inchecken en uitchecken in Experience Manager desktop app](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#how-app-works2)
>* [Videozelfstudie voor meer informatie over het in- en uitchecken van middelen](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html)

