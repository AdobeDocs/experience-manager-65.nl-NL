---
title: Apps ontwikkelen met PhoneGap CLI
seo-title: Apps ontwikkelen met PhoneGap CLI
description: Volg deze pagina voor meer informatie over het ontwikkelen van toepassingen met PhoneGap CLI.
seo-description: Volg deze pagina voor meer informatie over het ontwikkelen van toepassingen met PhoneGap CLI.
uuid: 9a66171d-19af-40db-9c07-f5dd9561e1b5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 4a034e15-3394-4be3-9e8e-bc894668946a
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---


# Toepassingen ontwikkelen met PhoneGap CLI{#developing-apps-with-phonegap-cli}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

Als ontwikkelaar kunt u uw app op elk gewenst moment op een apparaat of in een emulator uitvoeren, op voorwaarde dat u de ontwikkelomgeving hebt geconfigureerd.

Als u de volgende voorbeelden wilt uitvoeren, hebt u een systeem nodig waarop OSx (Mac) met Xcode wordt uitgevoerd of een Mac/Win/Linux-systeem waarop de Android-SDK is geïnstalleerd.

## Bootstrap uw ontwikkelomgeving {#bootstrap-your-development-environment}

[PhoneGap CLI instellen](https://docs.phonegap.com/en/4.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface)

Voor iOS: Voor de ontwikkeling van iPhones en iPads hebt u de Xcode-IDE van Apple nodig.

* Download deze gratis [hier](https://developer.apple.com/xcode/downloads/).
* [Handleiding bij PhoneGap iOS-platform](https://docs.phonegap.com/en/4.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide)

Voor Android: Voor het ontwikkelen voor iPhones en iPads hebt u de Android Stuido IDE van Google nodig.

* Download deze gratis [hier](https://developer.android.com/sdk/index.html).
* [Handleiding bij PhoneGap Android-platform](https://docs.phonegap.com/en/4.0.0/guide_platforms_android_index.md.html#Android%20Platform%20Guide)

## De bron {#download-the-source} downloaden

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

## De app ontwikkelen en laden (van bron) {#build-and-load-the-app-from-source}

PhoneGap CLI kan een platformproject tot stand brengen, de bron compileren, en app in één enkele bevel opstellen.

>[!NOTE]
>
>U kunt al deze stappen afzonderlijk doen, zie [CLI docs ](https://phonegap.com/blog/2014/11/13/phonegap-cli-3-6-3/) van PhoneGap.

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
>
Dit zal verifiëren dat u CLI van PhoneGap ontwikkelomgeving is correct in werking gesteld.

## Zuiver Javascripts met Safari en IOS zuiveren {#debug-javascripts-with-safari-and-ios-debug}

U kunt fouten in JavaScripts van uw app opsporen met de ontwikkelaarsprogramma&#39;s van Safari, net als bij een webtoepassing.

## Safari Developer Tools {#enable-safari-developer-tools} inschakelen

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
* Submenu iOS-simulator selecteren
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

Als u eenmaal geleerd hebt over het ontwikkelen van toepassingen met PhoneGap CLI, zie [Toegang tot apparaatfuncties](/help/mobile/phonegap-access-device-features.md).
