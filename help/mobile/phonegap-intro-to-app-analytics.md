---
title: App-prestaties bijhouden met Adobe Mobile Analytics
description: Met Adobe Mobile Services kunt u meer inzicht krijgen in hoe uw gebruikers uw mobiele apps gebruiken door gebruik, vastlopen van apps, apparaatdetails en zoveel andere belangrijke meetgegevens voor uw mobiele apps te volgen. Volg deze pagina voor meer informatie.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 7e358660-bc2f-4d8f-8d74-6cdb6c1ea7b5
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 0%

---

# App-prestaties bijhouden met Adobe Mobile Analytics{#track-app-performance-with-adobe-mobile-analytics}

{{ue-over-mobile}}

U wilt hogere klantenomzettingen en loyaliteit drijven.

U wilt relevante en boeiende ervaringen aan uw klanten leveren.

Wat doet uw AEM Mobile-app voor uw marketingcampagnes?

Hoe kunt u uw mobiele toepassingen verfijnen om de beste ervaring voor uw gebruikers te bieden?

Met Adobe Mobile Services kunt u meer inzicht krijgen in hoe uw gebruikers uw mobiele apps gebruiken door gebruik, vastlopen van apps, apparaatdetails en zoveel andere belangrijke meetgegevens voor uw mobiele apps te volgen.

Adobe Experience Manager Mobile geeft rechtstreeks vanaf het AEM Mobile Application Dashboard een glimp van de details van uw mobiele analysemogelijkheden. De **Mobiele Tegel van Metriek** in het dashboard verstrekt Real-Time Analytics voor uw mobiele toepassing, die ontwikkelaars, auteurs, en beheerders toestaat om een snelle glimp van de gezondheid van uw mobiele app te krijgen. Onder de omslagen, is het aandrijven van de analyse de [ Mobiele Analytics van de Adobe ](https://business.adobe.com/products/analytics/mobile-marketing.html) SDK. De Adobe Mobile Analytics SDK kan in uw toepassingen worden aangesloten of via een PhoneGap Bridge-plug-in voor webweergaven. Metrische gegevens worden verzameld en in cache geplaatst op het apparaat totdat het apparaat is aangesloten. Bij deze apparaten worden de gegevens naar de Adobe Mobile Services Cloud geduwd voor rapportage en analyse.

Adobe Mobile Analytics SDK biedt het volgende:

1. **inzameling van Gegevens voor mobiele kanalen** - verzamel uitvoerige gegevens voor uw mobiele websites en apps op alle belangrijke werkende systemen.
1. **Mobiele betrokkenheidsanalyse** - Begrijp gebruikersbetrokkenheid binnen uw mobiele app, website, of video, met inbegrip van hoe vaak de consumenten het kanaal lanceren, of zij kopen van het, en meer.
1. **Mobiele app dashboards en rapporten** - krijg gebruiksrapporten die levenscyclusmetriek voor uw apps en de metriek van de toepassingsopslag omvatten — zie tendensen voor gebruikers, lanceringen, gemiddelde zittingslengte, behoudlengte, en neerstortingen.
1. **Mobiele campagneanalyse** - kwantificeer de doeltreffendheid van mobiele-specifieke campagnes zoals SMS, mobiele onderzoeksadvertenties, mobiele vertoningsadvertenties, en QR codes.
1. **Geolocatieanalyse** - vind waar uw toepassingsgebruikers lanceren en met uw mobiele ervaringen door GPS plaats of punten van belang interactie aangaan.
1. **de analyse van het Schilderen** - zie hoe de gebruikers door uw app navigeren om te bepalen welke schermen en elementen UI gebruikers in dienst nemen en die gebruikers veroorzaken om weg te vallen.

Deze sectie beschrijft hoe [ AEM de Ontwikkelaars ](#developers) kunnen dan leren hoe te om AEM Mobile apps met analytische het volgen van instrumenten te voorzien.

Tot slot [ AEM Beheerders ](#administrators) leren om:

* een cloudservice voor de Adobe van mobiele services maken
* creeer een mobiele dienst config en associeer een rapportreeks
* associeer de mobiele dienst config aan een mobiele app
* metriek weergeven via het AEM Apps Command Center
* Wijs AMS SDK Config toe aan uw mobiele app

## Voor ontwikkelaars - Integreer Analytics in uw app {#for-developers-integrate-analytics-into-your-app}

**Vereiste:** AEM beheerders moeten de de wolk vormen van de Diensten van de Adobe Mobiele, [ zoals hieronder besproken ](#amscloudserviceconfig).

De ontwikkelaars zijn verantwoordelijk voor [ toevoegend analyses aan een AEM Mobile app ](/help/mobile/phonegap-add-analytics-to-apps.md) zonodig om te volgen, te rapporteren, en te begrijpen hoe uw gebruikers met uw mobiele toepassingsinhoud in dienst nemen en zeer belangrijke levenscyclusmetriek zoals lanceringen, tijd in app, en neerstortingstarief te meten.

## Voor Beheerders - vorm de Cloud Service van de Diensten van de Adobe Mobiele {#for-administrators-configure-the-adobe-mobile-services-cloud-service}

Om uit de Mobiele Diensten van de Adobe voordeel te halen, moet u de Cloud Service van de Mobiele Diensten van de AEM Adobe met uw de rekeningsinformatie van Adobe Analytics vormen. Het Centrum van het Bevel van Apps verstrekt een **Analyseer Metriek** tegel waar u de wolkendienst met uw mobiele app kunt tot stand brengen en associëren.

Configureer de cloudservice voor uw mobiele app door te klikken op het tandwielpictogram op de tegel Metrische gegevens analyseren.

![ chlimage_1-125 ](assets/chlimage_1-125.png)

Als u op het tandwielpictogram klikt in de tegel Metrische gegevens analyseren, wordt het modale dialoogvenster &#39;Analyse van mobiele services configureren&#39; geopend. Selecteer uw configuratie van &quot;Selecteer een Mobiele Configuratie van de Dienst&quot;drop-down. Als u een configuratie moet creëren, klik de moersleutelknoop.

Voor het maken van een Adobe Mobile Service Cloud Service zijn twee stappen nodig: de verbinding met de service en het selecteren van de rapportsuite die u aan de configuratie wilt toewijzen.

Klik om te beginnen op de knop &#39;+&#39; op de tegel Cloud Servicen beheren in het dashboard.

![ chlimage_1-126 ](assets/chlimage_1-126.png)

Na het klikken van &quot;**+**&quot;knoop, **voegt de** tovenaar van de Cloud Service toe wordt getoond.

![ chlimage_1-127 ](assets/chlimage_1-127.png)

Selecteer of maak een configuratie voor mobiele services door de vereiste velden in te vullen, zoals hieronder wordt weergegeven. Uw AEM beheerder vereist deze informatie om de verbinding met Adobe Mobile Services tot stand te brengen.

![ chlimage_1-128 ](assets/chlimage_1-128.png)

Nadat u de accountinstellingen voor mobiele services hebt voltooid, wordt u gevraagd een app te selecteren. Als u dit doet, wordt de Adobe Mobile Service Analytics die rapporteert aan die toepassing verbonden.

Selecteer de gewenste mobiele service en klik op Bijwerken om de configuratie van de mobiele service toe te wijzen en het dialoogvenster te sluiten.

Nu u de mobiele service config aan de AEM Mobile-app hebt gekoppeld, begint de tegel de metrische gegevens op te halen en begint de rapportage.

![ chlimage_1-129 ](assets/chlimage_1-129.png)

### Adobe Mobile Services SDK Config-bestand {#adobe-mobile-services-sdk-config-file}

Op dit moment is uw mobiele toepassing gekoppeld aan een cloudservice, maar de mobiele toepassing weet nog niet hoe de verzamelde mobiele meetgegevens naar Adobe Analytics moeten worden overgebracht. Als u de mobiele app wilt bekabelen naar Adobe Analytics, moet het bestand Adobe Mobile Services SDK Config worden toegevoegd aan Adobe Experience Manager.

Klik in de tegel Metrische gegevens analyseren op het pijlpictogram om de items in het menu AMS SDK Config downloaden/uploaden weer te geven.

![ chlimage_1-130 ](assets/chlimage_1-130.png)

De eerste stap is het verkrijgen van SDK Config van de Adobe Mobiele Diensten. Klik op &#39;AMS SDK Config downloaden&#39; om te worden omgeleid naar de website van Adobe Mobile Services waar u het configuratiebestand kunt downloaden. Nadat u het bestand ADBMobileConfig.json hebt ontvangen, klikt u op &quot;AMS SDK Config uploaden&quot; om het configuratiebestand in AEM te uploaden.

![ chlimage_1-131 ](assets/chlimage_1-131.png)

Klik op de knop &#39;Adobe voor mobiele services uploaden&#39; en blader naar het bestand ADBMobileConfig.json en klik op &#39;Uploaden&#39;.

Nu de mobiele app toegang heeft tot het bestand ADBMobileConfig.json, heeft deze de kennis over de manier waarop u weer met Adobe Analytics kunt communiceren en kunt rapporteren over de belangrijke metrische waarde die uw apps helpen doen slagen.

## Wat is de volgende? {#what-s-next}

1. [Mijn AEM Mobile-app-ervaring starten](/help/mobile/starting-aem-phonegap-app.md)
1. [De inhoud van mijn app beheren](/help/mobile/phonegap-manage-app-content.md)
1. [Mijn toepassing samenstellen](/help/mobile/building-app-mobile-phonegap.md)
1. [De prestaties van mijn app bijhouden met Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md)
1. [Een persoonlijke app-ervaring bieden met Adobe Target](/help/mobile/phonegap-aem-mobile-content-personalization.md)
1. [Belangrijke berichten naar mijn gebruikers sturen](/help/mobile/phonegap-push-notifications.md)
