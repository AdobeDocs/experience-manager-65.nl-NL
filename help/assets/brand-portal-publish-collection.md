---
title: Verzamelingen publiceren naar Brand Portal
seo-title: Publish collections to Brand Portal
description: Leer hoe u verzamelingen publiceert en publiceert naar Brand Portal.
seo-description: Learn how to publish and unpublish collections to Brand Portal.
uuid: 7de58548-4cfa-4a94-bac7-9e914dee9042
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
discoiquuid: 90e3fd0e-9bc3-4aff-8c7b-7408f5b940e8
docset: aem65
feature: Brand Portal
role: User
exl-id: 8f426012-d9ec-418e-8ab6-78e4aeff7538
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 26%

---

# Verzamelingen publiceren naar Brand Portal {#publish-collections-to-brand-portal}

Als beheerder van Adobe Experience Manager-middelen (AEM) kunt u verzamelingen publiceren naar het AEM Assets Brand Portal-exemplaar voor uw organisatie. U moet echter eerst AEM Assets integreren met Brand Portal. Zie [AEM Assets configureren met Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md) voor meer informatie.

Als u de oorspronkelijke verzameling in AEM Assets daarna wijzigt, worden de wijzigingen pas in Brand Portal doorgevoerd als u de verzameling opnieuw publiceert. Dit kenmerk zorgt ervoor dat wijzigingen in onderhanden werk niet beschikbaar zijn in Brand Portal. Alleen goedgekeurde wijzigingen die door een beheerder zijn gepubliceerd, zijn beschikbaar in Brand Portal.

>[!NOTE]
>
>Contentfragmenten kunnen niet naar Brand Portal worden gepubliceerd. Als u daarom inhoudsfragment(en) selecteert op AEM-auteur, dan **Publiceren naar Brand Portal** actie is niet beschikbaar.
>
>Als verzamelingen met inhoudsfragmenten worden gepubliceerd van AEM Author naar Brand Portal, wordt alle inhoud van de map, met uitzondering van inhoudsfragmenten, gerepliceerd naar de Brand Portal-interface.

## Een verzameling publiceren naar Brand Portal {#publish-a-collection-to-brand-portal}

1. Klik in de AEM Assets-gebruikersinterface op het AEM-logo.
1. Van **Navigatie** pagina, ga naar **Middelen > Verzamelingen**.
1. Selecteer in de console Verzamelingen de verzameling die u naar Brand Portal wilt publiceren.

   ![select_collection](assets/select_collection.png)

1. Klik op de werkbalk op **Publiceren naar Brand Portal**.
1. Klik in het bevestigingsdialoogvenster op **Publiceren**.
1. Sluit het bevestigingsbericht.
1. Meld u als beheerder aan bij Brand Portal. De gepubliceerde verzameling is beschikbaar in de Collections-console.

   ![published collection](assets/published_collection.png)

## De publicatie van verzamelingen ongedaan maken {#unpublish-collections}

U kunt de publicatie van verzamelingen die u van AEM Assets naar Brand Portal publiceert, ongedaan maken. Nadat u de publicatie van de oorspronkelijke verzameling hebt ongedaan gemaakt, is de kopie ervan niet meer beschikbaar voor Brand Portal-gebruikers.

1. Selecteer in de Collections-console van uw AEM Assets-instantie de verzameling die u wilt verwijderen.

   ![select_collection-1](assets/select_collection-1.png)

1. Klik op de werkbalk op **Verwijderen uit Brand Portal** pictogram.
1. Klik in het dialoogvenster op **Publiceren ongedaan maken**.
1. Sluit het bevestigingsbericht. De verzameling wordt verwijderd uit de Brand Portal-interface.
