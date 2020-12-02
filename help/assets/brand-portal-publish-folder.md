---
title: Mappen publiceren naar Brand Portal
seo-title: Mappen publiceren naar Brand Portal
description: Leer hoe u mappen naar Brand Portal publiceert en de publicatie ervan ongedaan maakt.
seo-description: Leer hoe u mappen naar Brand Portal publiceert en de publicatie ervan ongedaan maakt.
uuid: 350beb85-c0fb-4a1c-8597-c03592c02d3d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
discoiquuid: 39b8cf9b-afec-4c9a-8a5d-7fc87e643f26
docset: aem65
translation-type: tm+mt
source-git-commit: 9f923782d3d0a7bdf45b18e8025bd2d083acf77c
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 23%

---


# Mappen publiceren naar Brand Portal{#publish-folders-to-brand-portal}

Als beheerder van Adobe Experience Manager-middelen (AEM) kunt u elementen en mappen publiceren naar de AEM Assets Brand Portal-instantie (of de publicatieworkflow plannen op een latere datum of tijd) voor uw organisatie. U moet echter eerst AEM Assets integreren met Brand Portal. Zie [AEM Assets configureren met Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md) voor meer informatie.

Nadat u middelen of een omslag publiceert, is het beschikbaar aan gebruikers in het Portaal van het Merk.

Als u vervolgens wijzigingen aanbrengt in het oorspronkelijke element of de oorspronkelijke map in AEM Assets, worden de wijzigingen pas doorgevoerd in Brand Portal als u het element of de map opnieuw publiceert. Met deze functie zorgt u ervoor dat wijzigingen die momenteel worden uitgevoerd, niet beschikbaar zijn in Brand Portal. Alleen goedgekeurde wijzigingen die door een beheerder zijn gepubliceerd, zijn beschikbaar in Brand Portal.

## Mappen publiceren naar Brand Portal {#publish-folders-to-brand-portal-1}

1. Houd de muisaanwijzer in de AEM Assets-interface boven de gewenste map en selecteer de optie **Publiceren** in de snelhandelingen.

   U kunt ook de gewenste map selecteren en de volgende stappen volgen.

   ![publish2bp](assets/publish2bp.png)

1. **Mappen nu publiceren**

   Voer een van de volgende handelingen uit om de geselecteerde mappen naar Brand Portal te publiceren:

   * Selecteer **Snel publiceren** op de werkbalk. Selecteer vervolgens in het menu **Publiceren naar Brand Portal**.

   * Selecteer **Publicatie beheren** op de werkbalk.
   1. Selecteer **Publiceren naar Brand Portal** uit **Planning** **Now** en klik op **Volgende.******
   1. Bevestig uw selectie in **Scope** en klik **Publish aan Merk Portal**.

   Er verschijnt een bericht waarin wordt aangegeven dat de map in de wachtrij is geplaatst voor publicatie naar Brand Portal. Meld u aan bij de interface Brand Portal om de gepubliceerde map weer te geven.

   **Mappen later publiceren**

   De workflow voor publiceren naar Brand Portal van mappen met elementen naar een latere datum of tijd plannen:

   1. Als u middelen/mappen hebt geselecteerd om te publiceren, selecteert u **Publicatie beheren** in de werkbalk boven in het venster.
   1. Selecteer **Actie** **Publiceren naar Brand Portal**, selecteer **Planning** Later **Later**.

      ![publishlaterbp](assets/publishlaterbp.png)

   1. Selecteer een **activeringsdatum** en geef de tijd op. Klik op **Next**.
   1. Bevestig uw selectie in **Scope**. Klik op **Next**.
   1. Geef een workflowtitel op onder **Workflows**. Klik **Later publiceren**.

      ![manageschedulepub](assets/manageschedulepub.png)



## De publicatie van mappen op Brand Portal ongedaan maken {#unpublish-folders-from-brand-portal}

U kunt elke elementmap die naar Brand Portal is gepubliceerd, verwijderen door de publicatie ongedaan te maken van de instantie AEM-auteur. Nadat u de publicatie van de oorspronkelijke map ongedaan hebt gemaakt, is de kopie ervan niet meer beschikbaar voor Brand Portal-gebruikers.

U kunt de publicatie van mappen op Brand Portal snel ongedaan maken of deze later plannen. De publicatie van mappen met assets op Brand Portal ongedaan maken:

1. Selecteer in de AEM Assets-interface van de AEM-auteur-instantie de map die u wilt verwijderen.

   ![publish2bp-1](assets/publish2bp.png)

1. Klik op **Publicatie beheren** op de werkbalk.

1. **Publiceren via Brand Portal nu ongedaan maken**

   U kunt de publicatie van de gewenste map snel ongedaan maken via Brand Portal:

   1. Selecteer **Publicatie beheren** op de werkbalk.
   1. Selecteer **Publiceren ongedaan maken vanuit Brand Portal** uit **Planning** **Now** en klik op **Volgende.******
   1. Bevestig uw selectie in **Scope** en klik **Unpublish van het Portaal van het Merk**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Publiceren via Brand Portal later ongedaan maken**

   U kunt als volgt de publicatie van een map van Brand Portal naar een latere datum en tijd plannen:

   1. Selecteer **Publicatie beheren** op de werkbalk.
   1. Selecteer **Handeling** Publiceren via Brand Portal **ongedaan maken en selecteer** Later **uit** Planning **.**
   1. Selecteer een **Activeringsdatum** en geef de tijd op. Klik op **Next**.
   1. Bevestig uw selectie in **Scope** en klik **Next**.
   1. Geef een **Workflowtitel** op in **Workflows**. Klik **Publicatie later ongedaan maken.**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>De procedure voor het publiceren/openbaar maken van een middel van/naar Brand Portal is vergelijkbaar met de procedure voor een map.

