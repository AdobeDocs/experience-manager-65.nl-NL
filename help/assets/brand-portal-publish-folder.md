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
source-git-commit: 9c73abc3291f2847c705cb649d2993fb186b0993

---


# Mappen publiceren naar Brand Portal{#publish-folders-to-brand-portal}

Als beheerder van middelen van Adobe Experience Manager (AEM) kunt u elementen en mappen publiceren naar de AEM Assets Brand Portal-instantie (of de publicatieworkflow plannen op een latere datum/tijd) voor uw organisatie. U moet echter eerst AEM-middelen integreren met Brand Portal. Zie AEM Assets-integratie [configureren met Brand Portal](/help/assets/brand-portal-configuring-integration.md)voor meer informatie.

Nadat u middelen of een omslag publiceert, is het beschikbaar aan gebruikers in het Portaal van het Merk.

Als u de oorspronkelijke bron of map in AEM Assets wijzigt, worden de wijzigingen pas doorgevoerd in Brand Portal als u het element of de map opnieuw publiceert. Met deze functie zorgt u ervoor dat wijzigingen die momenteel worden uitgevoerd, niet beschikbaar zijn in Brand Portal. Alleen goedgekeurde wijzigingen die door een beheerder zijn gepubliceerd, zijn beschikbaar in Brand Portal.

## Mappen publiceren naar Brand Portal {#publish-folders-to-brand-portal-1}

1. Houd de muisaanwijzer boven de gewenste map in de interface AEM Assets en selecteer de optie **Publiceren** in de snelle handelingen.

   U kunt ook de gewenste map selecteren en de volgende stappen volgen.

   ![publish2bp](assets/publish2bp.png)

1. **Mappen nu publiceren**

   Voer een van de volgende twee handelingen uit om de geselecteerde mappen naar Brand Portal te publiceren:

   * Selecteer **Snel publiceren** op de werkbalk. Selecteer vervolgens in het menu **Publiceren naar Brand Portal**.

   * Selecteer Publicatie **beheren in de werkbalk**.
   1. Selecteer in **Actie** de optie **Publiceren naar Brand Portal**, in **Planning** de optie **Nu** en klik op **Volgende.**
   1. Bevestig uw selectie in **Toepassingsgebied** en klik op **Publiceren naar Brand Portal**.
   Er wordt een bericht weergegeven met de mededeling dat de map in de wachtrij is geplaatst voor publicatie naar Brand Portal. Meld u aan bij de interface Brand Portal om de gepubliceerde map weer te geven.

   **Mappen later publiceren**

   De workflow voor publiceren naar Brand Portal van mappen met elementen naar een latere datum of tijd plannen:

   1. Als u middelen/mappen hebt geselecteerd om te publiceren, selecteert u Publicatie **** beheren in de werkbalk boven in het scherm.
   1. Selecteer in **Actie** de optie **Publiceren naar Brand Portal** bij **Planning** de optie **Later**.

      ![uitgeverij](assets/publishlaterbp.png)

   1. Selecteer een **activeringsdatum** en geef de tijd op. Click **Next**.
   1. Bevestig uw selectie in **Bereik**. Click **Next**.
   1. Geef een workflowtitel op onder **Workflows**. Klik op Later **** publiceren.

      ![manageplannulepub](assets/manageschedulepub.png)



## Mappen van Brand Portal verwijderen {#unpublish-folders-from-brand-portal}

U kunt elke elementmap die naar Brand Portal is gepubliceerd, verwijderen door de publicatie ongedaan te maken van de instantie AEM-auteur. Nadat u de publicatie van de oorspronkelijke map ongedaan hebt gemaakt, is de kopie ervan niet meer beschikbaar voor gebruikers van het Brand Portal.

U kunt de publicatie van mappen op Brand Portal snel ongedaan maken of deze later plannen. De publicatie van middelenmappen op Brand Portal ongedaan maken:

1. Selecteer in de AEM Assets-interface in de AEM Author-instantie de map die u wilt verwijderen.

   ![publish2bp-1](assets/publish2bp.png)

1. Klik op Publicatie **beheren op de werkbalk**.

1. **Publiceren via Brand Portal nu ongedaan maken**

   U kunt de publicatie van de gewenste map snel ongedaan maken via Brand Portal:

   1. Selecteer Publicatie **beheren in de werkbalk**.
   1. Kies in **Handeling** de optie **Publicatie ongedaan maken op Brand Portal**, in **Planning** de optie **Nu** en klik op **Volgende.**
   1. Bevestig uw selectie in **Toepassingsgebied** en klik op **Publiceren ongedaan maken via Brand Portal**.
   ![bevestigen-ongedaan maken](assets/confirm-unpublish.png)

   **Publiceren via Brand Portal later ongedaan maken**

   U kunt als volgt de publicatie van een map van Brand Portal naar een latere datum en tijd plannen:

   1. Selecteer Publicatie **beheren in de werkbalk**.
   1. Selecteer in **Actie** de optie **Publiceren ongedaan maken in Brand Portal** en **kies** Later **in de planning**.
   1. Selecteer een **activeringsdatum** en geef de tijd op. Click **Next**.
   1. Bevestig uw selectie in **Toepassingsgebied** en klik op **Volgende**.
   1. Geef een **workflowtitel** op in **Workflows**. Klik op Later **publiceren ongedaan maken.**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>De procedure voor het publiceren/openbaar maken van een middel van/naar Brand Portal is vergelijkbaar met de procedure voor een map.

