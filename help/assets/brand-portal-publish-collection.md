---
title: Verzamelingen publiceren naar Brand Portal
seo-title: Verzamelingen publiceren naar Brand Portal
description: Leer hoe u verzamelingen publiceert en publiceert naar Brand Portal.
seo-description: Leer hoe u verzamelingen publiceert en publiceert naar Brand Portal.
uuid: 7de58548-4cfa-4a94-bac7-9e914dee9042
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
discoiquuid: 90e3fd0e-9bc3-4aff-8c7b-7408f5b940e8
docset: aem65
translation-type: tm+mt
source-git-commit: 9f923782d3d0a7bdf45b18e8025bd2d083acf77c
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 26%

---


# Verzamelingen publiceren naar Brand Portal {#publish-collections-to-brand-portal}

Als beheerder van Adobe Experience Manager-middelen (AEM) kunt u verzamelingen publiceren naar de AEM Assets Brand Portal-instantie voor uw organisatie. U moet echter eerst AEM Assets integreren met Brand Portal. Zie [AEM Assets configureren met Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md) voor meer informatie.

Als u verdere wijzigingen in de originele inzameling in AEM Assets aanbrengt, worden de veranderingen niet weerspiegeld in het Portaal van het Merk tot u de inzameling opnieuw publiceert. Dit kenmerk zorgt ervoor dat wijzigingen in onderhanden werk niet beschikbaar zijn in Brand Portal. Alleen goedgekeurde wijzigingen die door een beheerder zijn gepubliceerd, zijn beschikbaar in Brand Portal.

>[!NOTE]
>
>Contentfragmenten kunnen niet naar Brand Portal worden gepubliceerd. Als u daarom inhoudsfragment(en) selecteert op AEM-auteur, is de actie **Publiceren naar Brand Portal** niet beschikbaar.
>
>Als verzamelingen met inhoudsfragmenten van AEM-auteur naar Brand Portal worden gepubliceerd, wordt alle inhoud van de map behalve inhoudsfragmenten gerepliceerd naar de Brand Portal-interface.

## Een verzameling publiceren naar Brand Portal {#publish-a-collection-to-brand-portal}

1. Klik in de AEM Assets-gebruikersinterface op het AEM-logo.
1. Ga van **Navigation** pagina naar **Middelen > Verzamelingen**.
1. Van de console van Inzamelingen, selecteer de inzameling die u aan het Portaal van de Merk wilt publiceren.

   ![select_collection](assets/select_collection.png)

1. Van de toolbar, klik **publiceren aan het Portaal van het Merk**.
1. Klik in het bevestigingsdialoogvenster op **Publiceren**.
1. Sluit het bevestigingsbericht.
1. Meld u als beheerder aan bij Brand Portal. De gepubliceerde verzameling is beschikbaar in de Collections-console.

   ![published collection](assets/published_collection.png)

## De publicatie van verzamelingen ongedaan maken {#unpublish-collections}

U kunt de publicatie van verzamelingen die u publiceert van AEM Assets naar Brand Portal ongedaan maken. Nadat u de publicatie van de oorspronkelijke verzameling ongedaan hebt gemaakt, is de kopie ervan niet meer beschikbaar voor gebruikers van het Brand Portal.

1. Selecteer in de Collections-console van uw AEM Assets-instantie de verzameling die u wilt verwijderen.

   ![select_collection-1](assets/select_collection-1.png)

1. Klik op **Verwijderen uit Brand Portal**-pictogram op de werkbalk.
1. Klik in het dialoogvenster op **Publicatie ongedaan maken**.
1. Sluit het bevestigingsbericht. De verzameling wordt verwijderd uit de Brand Portal-interface.

