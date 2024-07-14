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
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [ leer meer ](/help/sites-developing/spa-overview.md).

Als u een On-Demand-app aan een Cloud Configuration koppelt, kan Adobe Experience Manager (AEM) rechtstreeks communiceren met een mobiel On-Demand-gehoste project door een tweerichtingskoppeling tot stand te brengen. Door uw app aan een mobiel On-Demand-project te koppelen, kunt u inhoud maken, zoals artikelen, banners en verzamelingen binnen AEM, maar u kunt deze inhoud ook op aanvraag aanbieden voor mobiele apparaten.

Vanaf dat punt wordt het publiceren, voorvertonen en beheren van inhoud mogelijk. U kunt ook bestaande Mobile On-Demand-inhoud importeren in AEM en inhoud bewerken.

## Cloudconfiguratie instellen {#setting-up-cloud-configuration}

>[!CAUTION]
>
>Voordat u de cloudconfiguratie voor uw On-Demand-app gaat configureren, moet u bekend zijn met AEM Mobile Provisioning and Configuring AEM Mobile On-demand Services Client.
>
>Voor details, zie [ Vestiging AEM Mobile On-demand Services ](/help/mobile/aem-mobile-setup.md) in de Administering sectie.

Om Mobiele Cloud Servicen op bestelling te vormen, klik de hoogste versnelling op de hoogste juiste hoek van de **Beheer de tegel van de Verbinding** van uw app dashboard.

U moet bekend zijn met het dashboard voor de app en de beschikbare tegels. Zie [ het Dashboard van de Toepassing van AEM Mobile ](/help/mobile/mobile-apps-ondemand-application-dashboard.md) voor meer details.

### Koppeling naar cloudconfiguratie instellen {#setting-up-link-to-cloud-configuration}

>[!CAUTION]
>
>Zorg ervoor dat u een bestaande configuratie voor on-demand clients en cloud hebt.
>
>Voor details, zie [ Vestiging AEM Mobile On-demand Services ](/help/mobile/aem-mobile-setup.md) in de Administering sectie.

In de volgende stappen wordt beschreven hoe u een koppeling naar de cloudconfiguratie instelt:

1. Van **Mobiel**, kies **Apps** en toen uw Mobiele On-Demand app van de catalogus.
1. Klik het tandwielpictogram op **leiden de tegel van de Verbinding**.

   ![ chlimage_1-65 ](assets/chlimage_1-65.png)

1. Ga reeds bestaande configuratie in of creeer door de **Titel van de Configuratie** in te gaan, **Identiteitskaart van het Apparaat**, en **Symbolisch van het Apparaat**.

   ![ chlimage_1-66 ](assets/chlimage_1-66.png)

1. Zodra uw **Identiteitskaart van het Apparaat** en **Symbolisch van het Apparaat** worden geverifieerd, kies uw project On-Demand van de lijst.

   Klik **voorleggen**.

   ![ chlimage_1-67 ](assets/chlimage_1-67.png)

   De **beheert de tegel van de Verbinding** toont uw Configuratie van de Wolk.

   ![ chlimage_1-68 ](assets/chlimage_1-68.png)

   >[!CAUTION]
   >
   >Als u probeert om te veranderen welk project deze App met wordt geassocieerd, terwijl het schakelen van project in het dashboard, zult u een waarschuwing voor de kwesties van de inhoudintegriteit zoals aangetoond in het hieronder cijfer ontvangen:

   ![ chlimage_1-69 ](assets/chlimage_1-69.png)

### De volgende stappen {#the-next-steps}

Nadat u de cloudconfiguratie voor uw app hebt geconfigureerd, raadpleegt u de volgende bronnen voor inhoudsbeheer:

* [Artikelen beheren](/help/mobile/mobile-on-demand-managing-articles.md)
* [Banners beheren](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verzamelingen beheren](/help/mobile/mobile-on-demand-managing-collections.md)
* [Gedeelde bronnen uploaden](/help/mobile/mobile-on-demand-shared-resources.md)
* [De inhoud publiceren/publiceren ongedaan maken](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
