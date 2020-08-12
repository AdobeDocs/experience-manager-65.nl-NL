---
title: De CDN-cache ongeldig maken via Dynamic Media
description: Door de CDN-inhoud (Content Delivery Network) in de cache te ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.6/ASSETS
topic-tags: dynamic-media
content-type: reference
translation-type: tm+mt
source-git-commit: 9e67e252348f471c052f6c3e88aea61d7a309241
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---


# De CDN-cache ongeldig maken via Dynamic Media {#invalidating-cdn-cache-for-dm-assets}

De dynamische activa van Media worden in het voorgeheugen ondergebracht door CDN (het Netwerk van de Levering van de Inhoud) voor snelle levering aan uw klanten. Wanneer u echter updates uitvoert voor deze elementen, kunt u deze wijzigingen direct op uw website toepassen. Door de CDN-cache te wissen of ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd. In plaats van te wachten op het verlopen van het geheime voorgeheugen gebruikend een waarde van TTL (Tijd aan Levend) (gebrek is 10 uren), kunt u een verzoek van binnen Dynamische Media verzenden om het geheime voorgeheugen te hebben onmiddellijk verlopen.

>[!IMPORTANT]
>
>Deze stappen zijn alleen van toepassing op Dynamic Media - Scene7-modus in AEM 6.5, Service Pack 6 of hoger. <!-- If you are using Dynamic Media in AEM 6.5, Service Pack 5 or earlier [use the steps found here](/help/assets/invalidate-cdn-cache-dm-classic.md). -->

Zie ook [Caching overzicht in Dynamische Media](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**Om uw CDN caching inhoud voor Dynamische activa van Media ongeldig te maken:**

1. Tik in AEM 6.5.6 of hoger op **[!UICONTROL Tools > Assets > CDN Invalidation.]**

   ![Functie voor CDN-validatie](/help/assets/assets-dm/cdn-invalidation-path.png)

1. Stel op de pagina CDN-validatie de gewenste opties in:

   | Optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Invalidate asset associated image presets in CDN]** | Wanneer u deze optie inschakelt, kunt u een of meer dynamische media-elementen selecteren, ongeacht het MIME-type en de bijbehorende voorinstellingen voor afbeeldingen, zodat de cache ongeldig wordt.<br>U kunt wel een of meer mappen met elementen selecteren, maar Adobe raadt deze aanpak niet aan. In plaats daarvan moet u afzonderlijke elementbestanden selecteren.<br>Ga verder met de volgende stap. |
   | **[!UICONTROL Invalidation based on template]** | Wanneer u deze optie inschakelt, kunt u de dynamische media-elementen en de sjabloon voor validatie selecteren die u eerder hebt gemaakt. Deze optie gebruiken met |
   | **[!UICONTROL Add Assets]** | Blah |
   | **[!UICONTROL Add URL]** | Voeg handmatig volledige URL-paden toe aan dynamische media-elementen waarvan u de cache wilt ongeldig maken. |

1. 
1. Tik op **[!UICONTROL Next.]**
1. 
