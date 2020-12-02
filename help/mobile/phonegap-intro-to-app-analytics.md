---
title: App-prestaties bijhouden met Adobe Mobile Analytics
seo-title: App-prestaties bijhouden met Adobe Mobile Analytics
description: Met Adobe Mobile Services kunt u meer inzicht krijgen in hoe uw gebruikers uw mobiele apps gebruiken door het gebruik, de vastgelopen apps, de details van apparaten en zoveel andere belangrijke meetgegevens voor uw mobiele apps te volgen. Volg deze pagina voor meer informatie.
seo-description: Met Adobe Mobile Services kunt u meer inzicht krijgen in hoe uw gebruikers uw mobiele apps gebruiken door het gebruik, de vastgelopen apps, de details van apparaten en zoveel andere belangrijke meetgegevens voor uw mobiele apps te volgen. Volg deze pagina voor meer informatie.
uuid: 139858c7-66a1-4fea-9f7e-4671b86f67e6
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 377548fa-987a-4a59-84a3-067a3541b6b2
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 0%

---


# Prestaties van toepassingen bijhouden met mobiele Adobe-analyse{#track-app-performance-with-adobe-mobile-analytics}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

U wilt hogere klantenomzettingen en loyaliteit drijven.

U wilt relevante en boeiende ervaringen aan uw klanten leveren.

Wat doet uw AEM Mobile-app voor uw marketingcampagnes?

Hoe kunt u uw mobiele toepassingen afstemmen om de beste ervaring voor uw gebruikers te bieden?

Met Adobe Mobile Services kunt u meer inzicht krijgen in hoe uw gebruikers uw mobiele apps gebruiken door het gebruik, de vastgelopen apps, de details van apparaten en zoveel andere belangrijke meetgegevens voor uw mobiele apps te volgen.

Adobe Experience Manager Mobile geeft rechtstreeks vanaf het AEM Mobile Application Dashboard een glimp van de details van uw mobiele analysemogelijkheden. De **Mobile Metrics Tile** in het dashboard biedt realtime analyses voor uw mobiele toepassing, zodat ontwikkelaars, auteurs en beheerders snel een voorsprong van de gezondheid van uw mobiele app kunnen krijgen. Onder de omslagen die de analyse aandrijven is [Adobe Mobiele Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) SDK. De SDK van Adobe Mobile Analytics kan in uw toepassingen worden aangesloten of via een PhoneGap bridge-insteekmodule voor webweergaven. Metrische gegevens worden verzameld en in cache geplaatst op het apparaat totdat het apparaat is aangesloten. Bij deze gegevens wordt de Adobe Mobile Services Cloud aangedrukt voor rapportage en analyse.

Adobe Mobile Analytics SDK biedt het volgende:

1. **Gegevensverzameling voor mobiele kanalen**  - Verzamel uitgebreide gegevens voor uw mobiele websites en toepassingen op alle grote besturingssystemen.
1. **Analyse**  van de mobiele betrokkenheid: begrijp de betrokkenheid van gebruikers binnen uw mobiele app, website of video, inclusief hoe vaak consumenten het kanaal starten, of ze er aankopen van maken en meer.
1. **Mobiele app-dashboards en -rapporten**  - Gebruiksrapporten met levenscyclusgegevens voor uw apps en maatgegevens voor de App Store — zie trends voor gebruikers, lanceringen, gemiddelde sessielengte, retentielengte en vastlopen.
1. **Analyse**  van mobiele campagnes - De doeltreffendheid van mobiele specifieke campagnes zoals SMS, mobiele onderzoeksadvertenties, mobiele vertoningsadvertenties, en QR codes kwantificeren.
1. **Geolocatieanalyse**  - Zoek waar uw gebruikers van de app uw mobiele beleving kunnen starten en interageren via de GPS-locatie of -punten.
1. **Analyse**  van het schilderen - zie hoe de gebruikers door uw app navigeren om te bepalen welke schermen en elementen UI gebruikers in dienst nemen en die gebruikers veroorzaken om weg te laten.

In deze sectie wordt beschreven hoe [AEM Developers](#developers) vervolgens leert hoe u AEM Mobile-toepassingen kunt optimaliseren met het bijhouden van analyses.

Tot slot [AEM Beheerders](#administrators) leren om:

* een cloudservice voor Adobe Mobile Services maken
* creeer een mobiele dienst config en associeer een rapportreeks
* associeer de mobiele dienst config aan een mobiele app
* metriek weergeven via het AEM Apps Command Center
* De configuratie van de AMS SDK toewijzen aan uw mobiele app

## Voor ontwikkelaars - Integreer Analytics in uw app {#for-developers-integrate-analytics-into-your-app}

**Vereiste:** AEM beheerders moeten de de wolkenconfiguratie van de Diensten van de Adobe Mobiele vormen,  [zoals hieronder](#amscloudserviceconfig) besproken.

Ontwikkelaars zijn verantwoordelijk voor het [toevoegen van analysemogelijkheden aan een AEM Mobile-app](/help/mobile/phonegap-add-analytics-to-apps.md), indien nodig, om te volgen, rapporteren en te begrijpen hoe gebruikers werken met inhoud van uw mobiele app en om belangrijke levenscyclusmetriek te meten, zoals lanceringen, tijd in app en crashsnelheid.

## Voor Beheerders - Configureer de Adobe Mobile Services-Cloud Service {#for-administrators-configure-the-adobe-mobile-services-cloud-service}

Als u gebruik wilt maken van Adobe Mobile Services, moet u de Cloud Service AEM Adobe Mobile Services configureren met uw Adobe Analytics-accountgegevens. Het Centrum van het Bevel van Apps verstrekt **Analyze Metrics** tegel waar u de wolkendienst tot stand kunt brengen en met uw mobiele app associëren.

Configureer de cloudservice voor uw mobiele app door te klikken op het tandwielpictogram op de tegel Metrische gegevens analyseren.

![chlimage_1-125](assets/chlimage_1-125.png)

Klik op het tandwielpictogram in de tegel Metrische gegevens analyseren om het modale dialoogvenster Analyse van mobiele services configureren te openen. Selecteer uw configuratie van &quot;Selecteer een Mobiele Configuratie van de Dienst&quot;drop-down. Als u een nieuwe configuratie moet creëren, klik de moersleutelknoop.

Voor het maken van een Adobe Mobile Service-cloudservice zijn er twee stappen nodig: de verbinding met de service en het selecteren van de rapportsuite die u aan de configuratie wilt toewijzen.

Klik om te beginnen op de knop &#39;+&#39; in het element Cloud Services beheren in het dashboard.

![chlimage_1-126](assets/chlimage_1-126.png)

Wanneer u op de knop &#39;**+**&#39; klikt, wordt de wizard **Cloud Service toevoegen** weergegeven.

![chlimage_1-127](assets/chlimage_1-127.png)

Selecteer of maak een nieuwe configuratie voor mobiele services door de vereiste velden in te vullen, zoals hieronder wordt weergegeven. Uw AEM beheerder zal deze informatie vereisen om de verbinding met de Mobiele Diensten van Adobe tot stand te brengen.

![chlimage_1-128](assets/chlimage_1-128.png)

Nadat u de accountinstellingen voor mobiele services hebt voltooid, wordt u gevraagd een app te selecteren. Als u dit doet, wordt de Adobe Mobile Service-analyse die wordt gerapporteerd, aan die toepassing gekoppeld.

Selecteer de gewenste mobiele service en klik op Bijwerken om de configuratie van de mobiele service toe te wijzen en het dialoogvenster te sluiten.

Nu u de configuratie van de mobiele service aan de AEM Mobile-app hebt gekoppeld, wordt de tegel opgehaald en wordt de rapportage gestart.

![chlimage_1-129](assets/chlimage_1-129.png)

### Adobe Mobile Services SDK Config-bestand {#adobe-mobile-services-sdk-config-file}

Op dit moment is uw mobiele toepassing gekoppeld aan een cloudservice, maar de mobiele toepassing weet nog niet hoe de verzamelde mobiele meetgegevens naar Adobe Analytics moeten worden overgebracht. Als u de mobiele app wilt overbrengen naar Adobe Analytics, moet het configuratiebestand van de Adobe Mobile Services SDK worden toegevoegd aan Adobe Experience Manager.

Klik in de tegel Metrische gegevens analyseren op het pijlpictogram om de menu-items van AMS SDK Config downloaden/uploaden weer te geven.

![chlimage_1-130](assets/chlimage_1-130.png)

De eerste stap bestaat uit het verkrijgen van de SDK-configuratie van Adobe Mobile Services. Als u op de configuratie van &#39;AMS SDK downloaden&#39; klikt, wordt u omgeleid naar de website van Adobe Mobile Services waar u het configuratiebestand kunt downloaden. Nadat u het bestand ADBMobileConfig.json hebt opgehaald, klikt u op de Configuratie van AMS SDK uploaden om het configuratiebestand in AEM te uploaden.

![chlimage_1-131](assets/chlimage_1-131.png)

Klik op de knop &#39;Adobe Mobile Services Application Config&#39; uploaden en blader naar het bestand ADBMobileConfig.json en klik op &#39;Uploaden&#39;.

Nu de mobiele app toegang heeft tot het bestand ADBMobileConfig.json, beschikt deze over de kennis van de manier waarop u weer met Adobe Analytics kunt communiceren en kunt beginnen met het rapporteren van die belangrijke metrische waarde die uw apps tot een succes zal maken.

## Wat nu? {#what-s-next}

1. [Mijn AEM Mobile-app starten](/help/mobile/starting-aem-phonegap-app.md)
1. [De inhoud van mijn app beheren](/help/mobile/phonegap-manage-app-content.md)
1. [Mijn toepassing samenstellen](/help/mobile/building-app-mobile-phonegap.md)
1. [De prestaties van mijn app bijhouden met Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md)
1. [Een persoonlijke app-ervaring bieden met Adobe Target](/help/mobile/phonegap-aem-mobile-content-personalization.md)
1. [Belangrijke berichten naar mijn gebruikers sturen](/help/mobile/phonegap-push-notifications.md)