---
title: Vorm uw Cloud Service van de Diensten van de Adobe Mobiele
description: Volg deze pagina om uw Cloud Service van de Diensten van de Adobe Mobiele te vormen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
legacypath: /content/docs/en/aem/6-1/develop/mobile-apps/apps/managing-aem-mobile-apps/configure-your-adobe-phonegap-build-cloud-service1
exl-id: 209c36f9-1a4b-4eea-8dde-22e0fc9718c1
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Vorm uw Cloud Service van de Diensten van de Adobe Mobiele {#configure-your-adobe-mobile-services-cloud-service}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [ leer meer ](/help/sites-developing/spa-overview.md).

De **Mobiele Tegel van Metriek** op het bevelcentrum verstrekt analyses in real time voor uw mobiele toepassing.

De [ Mobiele Analytics van de Adobe ](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) SDK wordt ter beschikking gesteld door een elektrisch toestel PhoneGap. Metrische gegevens worden verzameld en in cache geplaatst op het apparaat totdat het apparaat is aangesloten. Op dat moment worden de gegevens naar de Adobe Mobile Services Cloud geduwd voor rapportage en analyse.

Adobe Mobile Analytics SDK biedt het volgende:

1. **inzameling van Gegevens voor mobiele kanalen** - verzamel uitvoerige gegevens voor uw mobiele websites en apps op alle belangrijke werkende systemen.
1. **Mobiele betrokkenheidsanalyse** - Begrijp gebruikersbetrokkenheid binnen uw mobiele app, website, of video, met inbegrip van hoe vaak de consumenten het kanaal lanceren, of zij kopen van het, en meer.
1. **Mobiele app dashboards en rapporten** - krijg gebruiksrapporten die levenscyclusmetriek voor uw apps en de metriek van de toepassingsopslag omvatten — zie tendensen voor gebruikers, lanceringen, gemiddelde zittingslengte, behoudlengte, en neerstortingen.
1. **Mobiele campagneanalyse** - kwantificeer de doeltreffendheid van mobiele-specifieke campagnes zoals SMS, mobiele onderzoeksadvertenties, mobiele vertoningsadvertenties, en QR codes.
1. **Geolocatieanalyse** - vind waar uw toepassingsgebruikers lanceren en met uw mobiele ervaringen door GPS plaats of punten van belang interactie aangaan.
1. **de analyse van het Schilderen** - zie hoe de gebruikers door uw app navigeren om te bepalen welke schermen en elementen UI gebruikers in dienst nemen en die gebruikers veroorzaken om weg te vallen.

>[!CAUTION]
>
>De **Analyseer de vertoningen van Metriek** Tile in het dashboard, slechts als u de wolkendiensten hebt gevormd.

![ chlimage_1-22 ](assets/chlimage_1-22.png)

Metrische tegel AEM Command Center

## De Cloud Service configureren {#configuring-the-cloud-service}

Als u gebruik wilt maken van de Adobe Mobile Services Analytics, moet u de AEM Mobile Analytics Cloud Service configureren met uw Adobe Analytics-accountgegevens.

1. Klik op het hoogste rechterzijpictogram om de Cloud Servicen van **toe te voegen of uit te geven beheert Cloud Servicen** tegel van app dashboard.

   ![ chlimage_1-23 ](assets/chlimage_1-23.png)

1. **voeg of geef Cloud Servicen** het schermvertoningen toe uit. Selecteer **de Mobiele Diensten van de Adobe Mobiele** en klik **daarna**.

   ![ chlimage_1-24 ](assets/chlimage_1-24.png)

1. Kies een bestaande configuratie van de **Mobiele Diensten** of kies **creeer Configuratie** om te creëren.

   Voor nieuwe configuratie, ga de **Mobiele Eigenschappen van de Diensten** in en klik **verifieer.**

   ![ chlimage_1-25 ](assets/chlimage_1-25.png)

   Als de geloofsbrieven worden geverifieerd, verifieert **** knoopveranderingen in **Geverifieerd**. U kunt een mobiele dienst selecteren app van **een Mobiele Dienst van de App**.

   Klik **voorleggen** voor vestiging uw configuratie.

   ![ chlimage_1-26 ](assets/chlimage_1-26.png)

1. Als u een cloudconfiguratie hebt ingesteld, kunt u deze ook in het dashboard weergeven.

   ![ chlimage_1-27 ](assets/chlimage_1-27.png)

   >[!NOTE]
   >
   >Zodra u opstelling uw wolkenconfiguratie, kunt u **Analyseer Metriek** Tegel in uw app dashboard bekijken.

   ![ chlimage_1-28 ](assets/chlimage_1-28.png)
