---
title: Cloud Configuration
seo-title: Cloud Configuration
description: Als u een On-Demand-app aan een Cloud Configuration koppelt, kan Adobe Experience Manager (AEM) rechtstreeks communiceren met een mobiel On-Demand-project door een koppeling in twee richtingen tot stand te brengen. Volg deze pagina voor meer informatie.
seo-description: Als u een On-Demand-app aan een Cloud Configuration koppelt, kan Adobe Experience Manager (AEM) rechtstreeks communiceren met een mobiel On-Demand-project door een koppeling in twee richtingen tot stand te brengen. Volg deze pagina voor meer informatie.
uuid: f377f2af-864b-43df-9d42-4a5fd6cd70d5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
discoiquuid: d0d29b99-53d4-4b0d-947b-39d91b381de7
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Cloud Configuration{#cloud-configuration}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Als u een On-Demand-app aan een Cloud Configuration koppelt, kan Adobe Experience Manager (AEM) rechtstreeks communiceren met een mobiel On-Demand-project door een koppeling in twee richtingen tot stand te brengen. Door uw app aan een mobiel On-Demand-project te koppelen, kunt u inhoud maken, zoals artikelen, banners en verzamelingen in AEM, maar ook die inhoud leveren aan Mobiel On-Demand.

Vanaf dat punt wordt het publiceren, voorvertonen en beheren van inhoud mogelijk. U kunt ook bestaande Mobile On-Demand-inhoud importeren in AEM en inhoud bewerken.

## Cloudconfiguratie instellen {#setting-up-cloud-configuration}

>[!CAUTION]
>
>Voordat u de cloudconfiguratie voor uw On-Demand-app gaat configureren, moet u bekend zijn met AEM Mobile Provisioning en AEM Mobile On-Demand Services Client configureren.
>
>Zie [AEM Mobile On-Demand Services](/help/mobile/aem-mobile-setup.md) instellen in het gedeelte Beheer voor meer informatie.

Als u Mobile On-Demand Cloud Services wilt configureren, klikt u op de bovenste versnelling in de rechterbovenhoek van het element **Verbinding** beheren in het dashboard van de app.

U moet bekend zijn met het dashboard voor de app en de beschikbare tegels. Raadpleeg het [AEM Mobile Application Dashboard](/help/mobile/mobile-apps-ondemand-application-dashboard.md) voor meer informatie.

### Koppeling naar cloudconfiguratie instellen {#setting-up-link-to-cloud-configuration}

>[!CAUTION]
>
>Zorg ervoor dat u een bestaande configuratie voor on-demand clients en cloud hebt.
>
>Zie [AEM Mobile On-Demand Services](/help/mobile/aem-mobile-setup.md) instellen in het gedeelte Beheer voor meer informatie.

In de volgende stappen wordt beschreven hoe u een koppeling naar de cloudconfiguratie instelt:

1. Kies vanuit **mobiel** de optie **Apps** en vervolgens uw Mobile On-Demand-app in de catalogus.
1. Klik op het tandwielpictogram op de tegel **Verbinding** beheren.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Ga reeds bestaande configuratie in of creeer nieuwe door de Titel **van de** Configuratie, **Apparaat ID**, en **Token** van het Apparaat in te gaan.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Nadat de **apparaat-id** en het **apparaattoken** zijn geverifieerd, kiest u uw On-Demand-project in de lijst.

   Klik op **Verzenden**.

   ![chlimage_1-67](assets/chlimage_1-67.png)

   In het **tabblad Verbinding** beheren wordt de Cloud Configuration weergegeven.

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
* [De inhoud publiceren/verwijderen](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
