---
title: Mappen publiceren naar Brand Portal
description: Leer hoe u mappen publiceert en publiceert naar Brand Portal.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
docset: aem65
feature: Brand Portal
role: User
exl-id: 92a156f0-ce2a-4c83-bd57-0c29efbf784f
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 20%

---

# Mappen publiceren naar Brand Portal{#publish-folders-to-brand-portal}

Als beheerder van Adobe Experience Manager-middelen (AEM) kunt u elementen en mappen publiceren naar het AEM Assets Brand Portal-exemplaar (of de publicatieworkflow plannen op een latere datum/tijd) voor uw organisatie. U moet echter eerst AEM Assets integreren met Brand Portal. Zie [AEM Assets configureren met Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md) voor meer informatie.

Nadat u een middel of een omslag publiceert, is het beschikbaar aan gebruikers in Brand Portal.

Als u vervolgens wijzigingen aanbrengt in het oorspronkelijke element of de oorspronkelijke map in AEM Assets, worden de wijzigingen pas doorgevoerd in Brand Portal als u het element of de map opnieuw publiceert. Met deze functie zorgt u ervoor dat wijzigingen die momenteel worden uitgevoerd, niet beschikbaar zijn in Brand Portal. Alleen goedgekeurde wijzigingen die door een beheerder zijn gepubliceerd, zijn beschikbaar in Brand Portal.

## Mappen publiceren naar Brand Portal {#publish-folders-to-brand-portal-1}

1. Houd de muisaanwijzer boven de gewenste map in de AEM Assets-interface en selecteer **Publiceren** van de snelle acties.

   U kunt ook de gewenste map selecteren en de volgende stappen volgen.

   ![publish2bp](assets/publish2bp.png)

1. **Mappen nu publiceren**

   Voer een van de volgende handelingen uit om de geselecteerde mappen naar Brand Portal te publiceren:

   * Selecteer op de werkbalk de optie **Snel publiceren**. Selecteer vervolgens in het menu **Publiceren naar Brand Portal**.

   * Selecteer op de werkbalk de optie **Publicatie beheren**.

   1. Van **Handeling** selecteren **Publiceren naar Brand Portal**, van **Planning** selecteren **Nu** en klik op **Volgende.**
   1. Bevestig uw selectie in **Toepassingsgebied** en klik op **Publiceren naar Brand Portal**.

   Er verschijnt een bericht waarin wordt aangegeven dat de map in de wachtrij is geplaatst voor publicatie naar Brand Portal. Meld u aan bij de Brand Portal-interface om de gepubliceerde map weer te geven.

   **Mappen later publiceren**

   U kunt als volgt de publicatieworkflow van mappen met elementen naar Brand Portal plannen op een latere datum of tijd:

   1. Als u elementen/mappen hebt geselecteerd om te publiceren, selecteert u **Publicatie beheren** in de werkbalk bovenaan.
   1. Van **Handeling** selecteren **Publiceren naar Brand Portal**, van **Planning** selecteren **Later**.

      ![publishlaterbp](assets/publishlaterbp.png)

   1. Selecteer een **activeringsdatum** en geef de tijd op. Klik op **Next**.
   1. Bevestig uw selectie in **Toepassingsgebied**. Klik op **Next**.
   1. Geef een workflowtitel op onder **Workflows**. Klikken **Later publiceren**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Mappen uit Brand Portal verwijderen {#unpublish-folders-from-brand-portal}

U kunt elke elementmap die naar Brand Portal is gepubliceerd, verwijderen door de publicatie ervan uit AEM instantie Auteur ongedaan te maken. Nadat u de publicatie van de oorspronkelijke map ongedaan hebt gemaakt, is de kopie ervan niet meer beschikbaar voor Brand Portal-gebruikers.

U kunt de publicatie van mappen in Brand Portal snel ongedaan maken of deze later plannen. De publicatie van mappen met assets op Brand Portal ongedaan maken:

1. Selecteer in de AEM Assets-interface in AEM instantie Auteur de map die u wilt verwijderen.

   ![publish2bp-1](assets/publish2bp.png)

1. Klik op de werkbalk op **Publicatie beheren**.

1. **Publiceren vanuit Brand Portal nu ongedaan maken**

   U kunt de publicatie van de gewenste map snel ongedaan maken vanuit Brand Portal:

   1. Selecteer op de werkbalk de optie **Publicatie beheren**.
   1. Van **Handeling** selecteren **Publiceren vanuit Brand Portal ongedaan maken**, van **Planning** selecteren **Nu** en klik op **Volgende.**
   1. Bevestig uw selectie in **Toepassingsgebied** en klik op **Publiceren vanuit Brand Portal ongedaan maken**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Publiceren vanuit Brand Portal later ongedaan maken**

   U kunt als volgt de publicatie van een map van Brand Portal naar een latere datum en tijd plannen:

   1. Selecteer op de werkbalk de optie **Publicatie beheren**.
   1. Van **Handeling** selecteren **Publiceren vanuit Brand Portal ongedaan maken** en van **Planning** selecteren **Later**.
   1. Selecteer een **Activeringsdatum** en geeft u de tijd op. Klik op **Next**.
   1. Bevestig uw selectie in **Toepassingsgebied** en klik op **Volgende**.
   1. Geef een **Titel werkstroom** in **Workflows**. Klikken **Publicatie later ongedaan maken.**

      ![unpublishworkflows](assets/unpublishworkflows.png)

>[!NOTE]
>
>De procedure voor het publiceren/ongedaan maken van een middel van of naar Brand Portal is vergelijkbaar met de procedure voor het publiceren van een map.
