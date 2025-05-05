---
title: Publish-middelen naar Brand Portal
description: Leer hoe u middelen publiceert en publiceert naar Brand Portal.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
docset: aem65
feature: Brand Portal
role: User
exl-id: 76652a16-cad6-4e95-9e66-41efec452b03
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: cbf8a5ac22049b3372a8282b9c061d7abeacc5dc
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 39%

---

# Publish-middelen naar Brand Portal {#publish-assets-to-brand-portal}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

Als Adobe Experience Manager (AEM) Assets-beheerder kunt u elementen en mappen publiceren naar het AEM Assets Brand Portal-exemplaar (of de publicatieworkflow plannen op een latere datum/tijd) voor uw organisatie. U moet echter eerst AEM Assets configureren met Brand Portal. Zie [AEM Assets configureren met Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md) voor meer informatie.

Nadat de replicatie is gelukt, kunt u elementen, mappen en verzamelingen publiceren naar Brand Portal. Voer de volgende stappen uit om elementen te publiceren naar Brand Portal:

>[!NOTE]
>
>Adobe raadt gefaseerde publicatie aan, bij voorkeur niet tijdens piekuren, zodat de AEM-auteur niet te veel bronnen in beslag neemt.

1. Selecteer in de Assets-console de middelen/map die u wilt publiceren en klik op de optie **[!UICONTROL Quick Publish]** op de werkbalk.

   U kunt ook de elementen selecteren die u naar Brand Portal wilt publiceren.

   ![publish2bp-2](assets/publish2bp.png)

1. Voor het publiceren van de elementen naar Brand Portal zijn de volgende twee opties beschikbaar:
   * [Publish-middelen onmiddellijk](#publish-to-bp-now)
   * [Publish Assets later](#publish-to-bp-now)

## Publish-middelen nu {#publish-to-bp-now}

Voer een van de volgende handelingen uit om de geselecteerde assets naar Brand Portal te publiceren:

* Selecteer **[!UICONTROL Quick Publish]** in de werkbalk. Selecteer vervolgens **[!UICONTROL Publish to Brand Portal]** in het menu.

* Selecteer **[!UICONTROL Manage Publication]** in de werkbalk.

   1. Selecteer vervolgens **[!UICONTROL Action]** **[!UICONTROL Publish to Brand Portal]** bij **[!UICONTROL Scheduling]** Selecteren **[!UICONTROL Now]** . Klik op **[!UICONTROL Next]**.

   2. Bevestig uw selectie in **[!UICONTROL Scope]** en klik op **[!UICONTROL Publish to Brand Portal]** .

Er verschijnt een bericht waarin wordt aangegeven dat de assets in de wachtrij zijn geplaatst voor publicatie naar Brand Portal. Meld u aan bij de Brand Portal-interface om de gepubliceerde assets te bekijken.

## Publish Assets later {#publish-to-bp-later}

Voer de volgende handelingen uit om het publiceren van de assets naar Brand Portal op een latere datum of tijd te plannen:

1. Als u middelen/mappen hebt geselecteerd om te publiceren, selecteert u **[!UICONTROL Manage Publication]** in de werkbalk boven in het scherm.

1. Selecteer op de pagina **[!UICONTROL Manage Publication]** de optie **[!UICONTROL Publish to Brand Portal]** from **[!UICONTROL Action]** en selecteer **[!UICONTROL Later]** from **[!UICONTROL Scheduling]** .

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

1. Selecteer een **[!UICONTROL Activation date]** en geef de tijd op. Klik op **[!UICONTROL Next]**.

1. Selecteer een **activeringsdatum** en geef de tijd op. Klik op **Next**.

1. Geef een **[!UICONTROL Workflow title]** op in **[!UICONTROL Workflows]**. Klik op **[!UICONTROL Publish Later]**.

   ![publishworkflow](assets/publishworkflow.png)

Meld u nu aan bij Brand Portal om te zien of de gepubliceerde middelen beschikbaar zijn op de interface van Brand Portal.

![ bp_landingpage ](assets/bp_landingpage.png)

## Gepubliceerd bestand of map weergeven op Brand Portal {#view-published-file-folder}

1. Meld u aan bij de Brand Portal-interface om de gepubliceerde assets te bekijken (afhankelijk van uw geplande datum of tijd).

   ![ bp_landingpage ](assets/bp_landingpage.png)

1. De schakelaar aan de mening van de Lijst ![ mening van de Lijst ](assets/list-view.svg) om de huidige te zien publiceert status van de activa.

<!--2. On the [Asset Reports page](#https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/admin/asset-reports), you can see the current state of the report job, for example, Success, Failed, Queued, or Scheduled.-->

![ geproduceerde rapportstatus ](assets/report-status.JPG)
