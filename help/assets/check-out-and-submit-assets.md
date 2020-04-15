---
title: Digitale middelen inchecken en uitchecken voor bewerking
description: Leer hoe u middelen kunt uitchecken voor bewerking en ze weer kunt inchecken nadat de wijzigingen zijn voltooid.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# Bestanden in AEM DAM inchecken en uitchecken {#check-in-and-check-out-files-in-assets}

Met Adobe Experience Manager (AEM) Middelen kunt u elementen uitchecken en deze opnieuw inchecken nadat u alle wijzigingen hebt aangebracht. Nadat u een element hebt uitgecheckt, kunt u het element alleen bewerken, annoteren, publiceren, verplaatsen of verwijderen. Als u een element uitcheckt, vergrendelt u het element. Andere gebruikers kunnen geen van deze bewerkingen op het element uitvoeren totdat u het element weer incheckt bij AEM Assets. Ze kunnen echter wel de metagegevens van het vergrendelde element wijzigen.

Om activa te kunnen uitchecken/inchecken, hebt u schrijftoegang op hen nodig.

Met deze functie voorkomt u dat andere gebruikers de wijzigingen overschrijven die door een auteur zijn aangebracht en waarbij meerdere gebruikers samenwerken aan het bewerken van workflows in verschillende teams.

## Elementen uitchecken {#checking-out-assets}

1. Selecteer in de interface Elementen het element dat u wilt uitchecken. U kunt ook meerdere elementen selecteren om uit te checken.
1. From the toolbar, click **[!UICONTROL Checkout]**.
Met de optie **[!UICONTROL Uitchecken]** schakelt u over naar **[!UICONTROL Inchecken]**.
Meld u aan als een andere gebruiker om te controleren of andere gebruikers het uitgecheckte element kunnen bewerken. Er wordt een vergrendelingssymbool weergegeven op de miniatuur van het element dat u hebt uitgecheckt.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   Selecteer het element. Op de werkbalk worden geen opties weergegeven waarmee u elementen kunt bewerken, notities kunt aanbrengen, kunt publiceren of verwijderen.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   U kunt op Eigenschappen **** weergeven klikken om de metagegevens voor het vergrendelde element te bewerken.

1. Klik op **[!UICONTROL Bewerken]** om het element in de bewerkingsmodus te openen.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. Bewerk het element en sla de wijzigingen op. Snijd bijvoorbeeld de afbeelding bij en sla deze op.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   U kunt er ook voor kiezen om het element te annoteren of te publiceren.

1. Selecteer het bewerkte element in de [!DNL Assets] interface en klik op **[!UICONTROL Inchecken]** op de werkbalk. Het gewijzigde element wordt ingecheckt bij AEM Assets en is beschikbaar voor andere gebruikers voor bewerking.

## Geforceerd inchecken {#forced-check-in}

Beheerders kunnen elementen inchecken die door andere gebruikers zijn uitgecheckt.

1. Meld u als beheerder aan bij AEM Assets.
1. Selecteer in de interface Elementen een of meer elementen die door andere gebruikers zijn uitgecheckt.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klik in de werkbalk op **[!UICONTROL Vergrendelen]** opheffen. Het element is ingecheckt en kan worden bewerkt aan andere gebruikers.

>[!MORELIKETHIS]
>
>* [Inchecken en uitchecken in AEM-bureaubladtoepassing](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/using.html#how-app-works2)
>* [Videozelfstudie voor meer informatie over inchecken en uitchecken in AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/collaboration/checkin-checkout-technical-video-understand.html)

