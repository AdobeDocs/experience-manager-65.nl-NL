---
title: Uw Adobe Mobile Services-Cloud Service configureren
seo-title: Uw Adobe Mobile Services-Cloud Service configureren
description: Volg deze pagina om uw Adobe Mobiele Cloud Service van de Diensten te vormen.
seo-description: Volg deze pagina om uw Adobe Mobiele Cloud Service van de Diensten te vormen.
uuid: 21fe5b24-dc4d-4ee4-9e7f-ed4783baf276
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 962e9e98-a303-435b-a938-31319282e022
legacypath: /content/docs/en/aem/6-1/develop/mobile-apps/apps/managing-aem-mobile-apps/configure-your-adobe-phonegap-build-cloud-service1
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# Uw Adobe Mobile Services-Cloud Service {#configure-your-adobe-mobile-services-cloud-service} configureren

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

De **Mobile Metrics Tile** in het opdrachtcentrum biedt realtime analyses voor uw mobiele toepassing.

De [Adobe Mobile Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) SDK wordt beschikbaar gesteld via een PhoneGap-plug-in. Metrische gegevens worden verzameld en in cache geplaatst op het apparaat totdat het apparaat is aangesloten. Op dat moment worden de gegevens naar de Adobe Mobile Services Cloud geduwd voor rapportage en analyse.

Adobe Mobile Analytics SDK biedt het volgende:

1. **Gegevensverzameling voor mobiele kanalen**  - Verzamel uitgebreide gegevens voor uw mobiele websites en toepassingen op alle grote besturingssystemen.
1. **Analyse**  van de mobiele betrokkenheid: begrijp de betrokkenheid van gebruikers binnen uw mobiele app, website of video, inclusief hoe vaak consumenten het kanaal starten, of ze er aankopen van maken en meer.
1. **Mobiele app-dashboards en -rapporten**  - Gebruiksrapporten met levenscyclusgegevens voor uw apps en maatgegevens voor de App Store — zie trends voor gebruikers, lanceringen, gemiddelde sessielengte, retentielengte en vastlopen.
1. **Analyse**  van mobiele campagnes - De doeltreffendheid van mobiele specifieke campagnes zoals SMS, mobiele onderzoeksadvertenties, mobiele vertoningsadvertenties, en QR codes kwantificeren.
1. **Geolocatieanalyse**  - Zoek waar uw gebruikers van de app uw mobiele beleving kunnen starten en interageren via de GPS-locatie of -punten.
1. **Analyse**  van het schilderen - zie hoe de gebruikers door uw app navigeren om te bepalen welke schermen en elementen UI gebruikers in dienst nemen en die gebruikers veroorzaken om weg te laten.

>[!CAUTION]
>
>De **Metriek analyseren** Blokvertoningen in het dashboard, slechts als u de wolkendiensten hebt gevormd.

![chlimage_1-22](assets/chlimage_1-22.png)

Metrische tegel AEM Command Center

## De Cloud Service {#configuring-the-cloud-service} configureren

Als u gebruik wilt maken van Adobe Mobile Services Analytics, moet u de AEM Mobile Analytics Cloud Service configureren met uw Adobe Analytics-accountgegevens.

1. Klik op het rechterbovenpictogram om de Cloud Services toe te voegen of te bewerken vanuit de tegel **Cloud Services beheren** van het dashboard van de app.

   ![chlimage_1-23](assets/chlimage_1-23.png)

1. De **Cloud Services toevoegen of bewerken** schermvertoningen. Selecteer **Mobiele services Adobe** en klik op **Volgende**.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Kies een bestaande configuratie in **Mobiele services** of kies **Configuratie maken** om een nieuwe te maken.

   Voor nieuwe configuratie voert u **Eigenschappen voor mobiele services** in en klikt u **Verifiëren.**

   ![chlimage_1-25](assets/chlimage_1-25.png)

   Als de referenties zijn geverifieerd, verandert de **Verify** knoop in **Verified**. U kunt een mobiele service-app kiezen uit **Selecteer een Mobile App Service**.

   Klik **Submit** voor vestiging uw configuratie.

   ![chlimage_1-26](assets/chlimage_1-26.png)

1. Als u een cloudconfiguratie hebt ingesteld, kunt u deze ook in het dashboard weergeven.

   ![chlimage_1-27](assets/chlimage_1-27.png)

   >[!NOTE]
   >
   >Nadat u de cloudconfiguratie hebt ingesteld, kunt u de **Metriek analyseren** Naast elkaar weergeven in het dashboard van de app.

   ![chlimage_1-28](assets/chlimage_1-28.png)

