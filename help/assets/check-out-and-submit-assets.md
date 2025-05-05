---
title: Bestanden in- en uitchecken in  [!DNL Assets]
description: Leer hoe u middelen kunt uitchecken voor bewerking en ze weer kunt inchecken nadat de wijzigingen zijn voltooid.
contentOwner: AG
role: User
feature: Asset Management
exl-id: 544ef73c-4e4b-433f-a173-fdf1c8f45d8e
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Bestanden in [!DNL Experience Manager] DAM inchecken en uitchecken {#check-in-and-check-out-files-in-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/check-out-and-submit-assets.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

Met [!DNL Adobe Experience Manager Assets] kunt u elementen uitchecken en deze opnieuw inchecken nadat u alle wijzigingen hebt aangebracht. Nadat u een element hebt uitgecheckt, kunt u het element alleen bewerken, annoteren, publiceren, verplaatsen of verwijderen. Als u een element uitcheckt, vergrendelt u het element. Andere gebruikers kunnen geen van deze bewerkingen op het element uitvoeren totdat u het element weer incheckt bij [!DNL Assets] . Ze kunnen echter wel de metagegevens van het vergrendelde element wijzigen.

Om activa te kunnen uitchecken/inchecken, hebt u schrijftoegang op hen nodig.

Met deze functie voorkomt u dat andere gebruikers de wijzigingen overschrijven die door een auteur zijn aangebracht en waarbij meerdere gebruikers samenwerken aan het bewerken van workflows in verschillende teams.

## Elementen uitchecken {#checking-out-assets}

1. Selecteer in de gebruikersinterface van [!DNL Assets] het element dat u wilt uitchecken. U kunt ook meerdere elementen selecteren om uit te checken.
1. Klik in de werkbalk op **[!UICONTROL Checkout]** . Met de optie **[!UICONTROL Checkout]** schakelt u over naar **[!UICONTROL Checkin]** .
Meld u aan als een andere gebruiker om te controleren of andere gebruikers het uitgecheckte element kunnen bewerken. Er wordt een vergrendelingssymbool weergegeven op de miniatuur van het element dat u hebt uitgecheckt.

   ![ chlimage_1-471 ](assets/chlimage_1-471.png)

   Selecteer het element. Op de werkbalk worden geen opties weergegeven waarmee u elementen kunt bewerken, notities kunt aanbrengen, kunt publiceren of verwijderen.

   ![ chlimage_1-472 ](assets/chlimage_1-472.png)

   Klik op **[!UICONTROL View Properties]** als u de metagegevens voor het vergrendelde element wilt bewerken.

1. Klik op **[!UICONTROL Edit]** om het element te openen in de bewerkingsmodus.

   ![ chlimage_1-473 ](assets/chlimage_1-473.png)

1. Bewerk het element en sla de wijzigingen op. Snijd bijvoorbeeld de afbeelding bij en sla deze op.

   ![ chlimage_1-474 ](assets/chlimage_1-474.png)

   U kunt er ook voor kiezen om het element te annoteren of te publiceren.

1. Selecteer het bewerkte element in de interface van [!DNL Assets] en klik op **[!UICONTROL Checkin]** op de werkbalk. Het gewijzigde element is ingecheckt in [!DNL Assets] en is beschikbaar voor andere gebruikers voor bewerking.

## Geforceerd inchecken {#forced-check-in}

Beheerders kunnen elementen inchecken die door andere gebruikers zijn uitgecheckt.

1. Meld u aan bij [!DNL Assets] als beheerder.
1. Selecteer in de gebruikersinterface van [!DNL Assets] een of meer elementen die door andere gebruikers zijn uitgecheckt.

   ![ chlimage_1-476 ](assets/chlimage_1-476.png)

1. Klik in de werkbalk op **[!UICONTROL Release Lock]** . Het element is ingecheckt en kan worden bewerkt aan andere gebruikers.

## Aanbevolen werkwijzen en beperkingen {#tips-limitations}

* Het is mogelijk om a *omslag* te schrappen die uitgecheckte activadossiers bevat. Voordat u een map verwijdert, moet u controleren of er geen digitale elementen zijn uitgecheckt door gebruikers.

>[!MORELIKETHIS]
>
>* [ Begrijp controle binnen en controle in  [!DNL Experience Manager]  Desktop app ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=nl-NL#how-app-works2)
>* [ Videozelfstudie om controle binnen te begrijpen en uit te checken  [!DNL Assets] ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html?lang=nl-NL)
