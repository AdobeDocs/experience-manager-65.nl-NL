---
title: Cloud Configuration
description: Als u een On-Demand-app aan een Cloud Configuration koppelt, kan Adobe Experience Manager (AEM) rechtstreeks communiceren met een mobiel On-Demand-gehoste project door een tweerichtingskoppeling tot stand te brengen. Volg deze pagina voor meer informatie.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
exl-id: 37428543-c310-4712-a4ec-1f482579fb4b
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Cloud Configuration{#cloud-configuration}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Als u een On-Demand-app aan een Cloud Configuration koppelt, kan Adobe Experience Manager (AEM) rechtstreeks communiceren met een mobiel On-Demand-gehoste project door een tweerichtingskoppeling tot stand te brengen. Door uw app aan een mobiel On-Demand-project te koppelen, kunt u inhoud maken, zoals artikelen, banners en verzamelingen binnen AEM, maar u kunt deze inhoud ook op aanvraag aanbieden voor mobiele apparaten.

Vanaf dat punt wordt het publiceren, voorvertonen en beheren van inhoud mogelijk. U kunt ook bestaande Mobile On-Demand-inhoud importeren in AEM en inhoud bewerken.

## Cloudconfiguratie instellen {#setting-up-cloud-configuration}

>[!CAUTION]
>
>Voordat u de cloudconfiguratie voor uw On-Demand-app gaat configureren, moet u bekend zijn met AEM Mobile Provisioning and Configuring AEM Mobile On-demand Services Client.
>
>Zie voor meer informatie [AEM Mobile On-demand Services instellen](/help/mobile/aem-mobile-setup.md) in de sectie Beheer.

Als u mobiele Cloud Servicen op aanvraag wilt configureren, klikt u op de bovenste versnelling in de rechterbovenhoek van het dialoogvenster **Verbinding beheren** element uit het dashboard van uw app.

U moet bekend zijn met het dashboard voor de app en de beschikbare tegels. Zie [AEM Mobile-toepassingsdashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md) voor meer informatie .

### Koppeling naar cloudconfiguratie instellen {#setting-up-link-to-cloud-configuration}

>[!CAUTION]
>
>Zorg ervoor dat u een bestaande configuratie voor on-demand clients en cloud hebt.
>
>Zie voor meer informatie [AEM Mobile On-demand Services instellen](/help/mobile/aem-mobile-setup.md) in de sectie Beheer.

In de volgende stappen wordt beschreven hoe u een koppeling naar de cloudconfiguratie instelt:

1. Van **Mobiel**, kiest u **Apps** en vervolgens uw Mobile On-Demand-app uit de catalogus.
1. Klik op het tandwielpictogram op het tabblad **Verbinding beheren** tegel.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Voer de bestaande configuratie in of maak een configuratie door de **Configuratietitel**, **Apparaat-id**, en **Apparaattoken**.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Eenmaal uw **Apparaat-id** en **Apparaattoken** Kies uw On-Demand-project in de lijst.

   Klikken **Verzenden**.

   ![chlimage_1-67](assets/chlimage_1-67.png)

   De **Verbinding beheren** De tegel toont uw Configuratie van de Wolk.

   ![chlimage_1-68](assets/chlimage_1-68.png)

   >[!CAUTION]
   >
   >Als u probeert om te veranderen welk project deze App met wordt geassocieerd, terwijl het schakelen van project in het dashboard, zult u een waarschuwing voor de kwesties van de inhoudintegriteit zoals aangetoond in het hieronder cijfer ontvangen:

   ![chlimage_1-69](assets/chlimage_1-69.png)

### De volgende stappen {#the-next-steps}

Nadat u de cloudconfiguratie voor uw app hebt geconfigureerd, raadpleegt u de volgende bronnen voor inhoudsbeheer:

* [Artikelen beheren](/help/mobile/mobile-on-demand-managing-articles.md)
* [Banners beheren](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verzamelingen beheren](/help/mobile/mobile-on-demand-managing-collections.md)
* [Gedeelde bronnen uploaden](/help/mobile/mobile-on-demand-shared-resources.md)
* [De inhoud publiceren/publiceren ongedaan maken](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
