---
title: Apps ontwikkelen met PhoneGap CLI
seo-title: Developing Apps with PhoneGap CLI
description: Volg deze pagina voor meer informatie over het ontwikkelen van toepassingen met PhoneGap CLI.
seo-description: Follow this page to learn about developing apps with PhoneGap CLI.
uuid: 9a66171d-19af-40db-9c07-f5dd9561e1b5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 4a034e15-3394-4be3-9e8e-bc894668946a
exl-id: fbeceb70-b199-478b-907b-253ed212ff99
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%

---

# Apps ontwikkelen met PhoneGap CLI{#developing-apps-with-phonegap-cli}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

Als ontwikkelaar kunt u uw app op elk gewenst moment op een apparaat of in een emulator uitvoeren, op voorwaarde dat u de ontwikkelomgeving hebt geconfigureerd.

Voor het uitvoeren van de volgende voorbeelden hebt u een systeem nodig waarop OSx (Mac) met Xcode wordt uitgevoerd, of een Mac/Win/Linux-systeem waarop de Android SDK is geïnstalleerd.

## Bootstrap uw ontwikkelomgeving {#bootstrap-your-development-environment}

[PhoneGap CLI instellen](https://docs.phonegap.com/en/4.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface)

Voor iOS: Voor het ontwikkelen voor iPhones en iPads hebt u Apple Xcode IDE nodig.

* Gratis downloaden [hier](https://developer.apple.com/xcode/downloads/).
* [Handleiding bij PhoneGap iOS-platform](https://docs.phonegap.com/en/4.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide)

Voor Android: Voor het ontwikkelen voor iPhones en iPads hebt u Google Android Stuido IDE nodig.

* Gratis downloaden [hier](https://developer.android.com/sdk/index.html).
* [Handleiding bij PhoneGap Android-platform](https://docs.phonegap.com/en/4.0.0/guide_platforms_android_index.md.html#Android%20Platform%20Guide)

## De bron downloaden {#download-the-source}

Als u de ontwikkelomgeving hebt opgestart, downloadt u de bron van de AEM App Build Tile:

* Klik op de PhoneGap Build tieldropdown chevron.

![chlimage_1-45](assets/chlimage_1-45.png)

* Klik op Bron downloaden.
* Selecteer de gewenste bron in het modaal van de Download Source.

![chlimage_1-46](assets/chlimage_1-46.png)

>[!NOTE]
>
>De ontwikkelingsbron bevat de meest recente status van uw app en bevat niet-gefaseerde wijzigingen. Gebruik de Staging-bron voor het samenstellen van releasekandidaten voor het indienen bij leveranciers van App Store.
>
>Als u uw app nooit plaatst, wordt de testworkflow geactiveerd wanneer u Staging selecteert (tip: deze verschijnt als een gefaseerde app in de PhoneGap Enterprise Viewer-app (beschikbaar in de AppStore en Google PlayStore).

* Klik op Downloaden en sla het ZIP-bestand op uw computer op.
* Extraheer het gedownloade ZIP-bestand naar uw werkruimte.

## App maken en laden (van bron) {#build-and-load-the-app-from-source}

PhoneGap CLI kan een platformproject tot stand brengen, de bron compileren, en app in één enkele bevel opstellen.

>[!NOTE]
>
>U kunt al deze stappen afzonderlijk uitvoeren, zie [PhoneGap CLI-documenten](https://phonegap.com/blog/2014/11/13/phonegap-cli-3-6-3/).

1. Controleer of u PhoneGap CLI hebt geïnstalleerd, zie hierboven.
1. Navigeer in een consolevenster (of terminalvenster) naar de hoofdmap van de uitgepakte bron.
1. Voer de volgende opdracht in:

```xml
phonegap run android

// -- or -- //

phonegap run ios
```

>[!NOTE]
>
>Als er op dit moment problemen zijn, ga dan terug naar de basis om problemen op te lossen -
>
>1. Een nieuwe map maken (mkdir-test)
>1. Navigeren naar deze nieuwe map (cd-test)
>1. &#39;phonegap create helloWorld&#39; uitvoeren
>1. Navigeer in helloWorld (cd helloWorld)
>1. Voer &#39;phonegap run android (of vervang android door ios as above) uit.
>1. Emulator opent de uitvoering van de zojuist gemaakte PhoneGap-app met de tekst &#39;Apparaatklaar&#39; als de JavaScript-bridge naar native actief is.

>
>Dit zal verifiëren dat u CLI van PhoneGap ontwikkelomgeving is correct in werking gesteld.

## Fouten opsporen in JavaScript met Safari- en IOS-foutopsporing {#debug-javascripts-with-safari-and-ios-debug}

U kunt fouten in JavaScripts van uw app opsporen met de ontwikkelaarsprogramma&#39;s van Safari, net als bij een webtoepassing.

## Safari Developer Tools inschakelen {#enable-safari-developer-tools}

De gereedschappen voor ontwikkelaars inschakelen:

* Safari-voorkeuren openen

   * Klik op Safari in de menubalk
   * Klik op Voorkeuren

* Klik op Geavanceerd in het venster Voorkeuren

![chlimage_1-47](assets/chlimage_1-47.png)

* Schakel &quot;Ontwikkelmenu tonen in menubalk&quot; in
* Het venster Voorkeuren sluiten

## Safari verbinden met iOS {#connect-safari-to-ios}

U kunt Safari verbinden met een iOS-apparaat of emulator.

* Navigeer in een consolevenster naar de hoofdmap van de uitgepakte bron.
* Voer de volgende opdracht in om uw toepassing op uw apparaat of emulator te starten.

```xml
phonegap run <platform> --device

// -- or -- //

phonegap run <platform> --emulator
```

* Safari openen
* Klik op Ontwikkelen in de menubalk
* Het submenu iOS Simulator selecteren
* Klik op home.html

![chlimage_1-48](assets/chlimage_1-48.png)

## Foutopsporing in JavaScript met Safari&#39;s webcontrole {#debug-javascript-with-safari-s-web-inspector}

U kunt onderbrekingspunten overal in de bron instellen. Wanneer u met uw emulator of apparaat werkt, stopt de uitvoering van uw app bij deze onderbrekingspunten. U kunt door de uitvoering stappen en de waarden in variabelen inspecteren.

* Klik Middelen in het venster van de Inspecteur van het Web
* Navigeren in de bronstructuur en klikken op het gewenste bronbestand
* Klik op het regelnummer naast om een onderbrekingspunt toe te voegen
* Interactie met apparaat of emulator

![chlimage_1-49](assets/chlimage_1-49.png)

* Gebruik de bedieningsknoppen om door te gaan met uitvoeren, stap over, stap in en stap uit van methoden:

![](do-not-localize/chlimage_1-4.png)

>[!NOTE]
>
>Houd de muis boven de huidige methode om de waarden van variabelen weer te geven.

## De volgende stappen {#the-next-steps}

Als u eenmaal geleerd hebt over het ontwikkelen van toepassingen met PhoneGap CLI, raadpleegt u [Apparaatfuncties openen](/help/mobile/phonegap-access-device-features.md).
