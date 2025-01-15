---
title: Apps ontwikkelen met PhoneGap CLI
description: Leer hoe u met PhoneGap CLI toepassingen voor mobiele apparaten ontwikkelt met behulp van een 'bootstrapped' ontwikkelomgeving.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: fbeceb70-b199-478b-907b-253ed212ff99
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---

# Apps ontwikkelen met PhoneGap CLI{#developing-apps-with-phonegap-cli}

{{ue-over-mobile}}

Als ontwikkelaar kunt u uw app op elk gewenst moment op een apparaat of in een emulator uitvoeren, op voorwaarde dat u de ontwikkelomgeving hebt geconfigureerd.

Voor het uitvoeren van de volgende voorbeelden hebt u een systeem nodig waarop macOS X met Xcode wordt uitgevoerd, of een Mac/Win/Linux-systeem waarop de Android™ SDK is geïnstalleerd.

## Bootstrap uw ontwikkelomgeving {#bootstrap-your-development-environment}

PhoneGap CLI instellen (`https://docs.phonegap.com/en/4.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface`)

Voor iOS: voor de ontwikkeling van iPhones en iPads hebt u Apple Xcode-IDE nodig.

* Download het voor vrije [ hier ](https://idmsa.apple.com/IDMSWebAuth/signin?appIdKey=891bd3417a7776362562d2197f89480a8547b108fd934911bcbea0110d07f757&amp;path=%2Fdownload%2F&amp;rv=1).
* PhoneGap iOS-platformhulplijn (`https://docs.phonegap.com/en/4.0.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide`)

Voor Android™: voor de ontwikkeling van iPhones en iPads hebt u Android™ Stuido IDE van Google nodig.

* Download het voor vrije [ hier ](https://developer.android.com/studio).
* PhoneGap Android™-platformhandleiding (`https://docs.phonegap.com/en/4.0.0/guide_platforms_android_index.md.html#Android%20Platform%20Guide`)

## De Source downloaden {#download-the-source}

Wanneer u uw ontwikkelomgeving met succes hebt versneld, downloadt u de bron van de AEM App Build Tile:

* Klik op de vervolgkeuzelijst PhoneGap Build-tegel.

![ chlimage_1-45 ](assets/chlimage_1-45.png)

* Klik op Source downloaden.
* Selecteer de gewenste bron in het modaal station van Source downloaden.

![ chlimage_1-46 ](assets/chlimage_1-46.png)

>[!NOTE]
>
>De ontwikkelingsbron bevat de meest recente status van uw app, maar inclusief niet-gefaseerde wijzigingen. Gebruik de Staging-bron voor het samenstellen van releasekandidaten voor het indienen bij leveranciers van App Store.
>
>Als u uw app nooit in het werkgebied plaatst, wordt door het selecteren van Staging de testworkflow (tip: wordt weergegeven als een gefaseerde app in de PhoneGap Enterprise Viewer App die beschikbaar is in de AppStore en Google PlayStore) geactiveerd.

* Klik op Downloaden en sla het ZIP-bestand op uw computer op.
* Extraheer het gedownloade ZIP-bestand naar uw werkruimte.

## App maken en laden (van bron) {#build-and-load-the-app-from-source}

PhoneGap CLI kan een platformproject tot stand brengen, de bron compileren, en app in één enkele bevel opstellen.

>[!NOTE]
>
>U kunt al deze stappen afzonderlijk doen, zie CLI documenten PhoneGap (`https://phonegap.com/blog/2014/11/13/phonegap-cli-3-6-3/`).

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
>Als u op dit punt problemen hebt, ga terug naar grondbeginselen om problemen op te lossen -
>
>1. Een map maken (mkdir-test)
>1. Navigeren naar deze nieuwe map (cd-test)
>1. Uitvoeren `phonegap create helloWorld`
>1. Navigeer in helloWorld (cd helloWorld)
>1. Voer `phonegap run android` uit (of vervang Android™ door iOS zoals hierboven beschreven).
>1. Emulator opent het uitvoeren van uw nieuwe PhoneGap App, die &quot;Apparaat Klaar&quot;zegt als JavaScript Bridge aan inheems operationeel is.
>
>Dit het oplossen van problemen verifieert dat uw CLI van PhoneGap ontwikkelomgeving correct loopt.

## Foutopsporing in JavaScript met Safari en IOS {#debug-javascripts-with-safari-and-ios-debug}

U kunt fouten in de JavaScript van uw app opsporen met de ontwikkelaarsprogramma&#39;s van Safari, net als bij een webtoepassing.

## Safari Developer Tools inschakelen {#enable-safari-developer-tools}

De gereedschappen voor ontwikkelaars inschakelen:

* Safari-voorkeuren openen

   * Klik op Safari in de menubalk
   * Klik op Voorkeuren

* Klik op Geavanceerd in het venster Voorkeuren

![ chlimage_1-47 ](assets/chlimage_1-47.png)

* Schakel &quot;Ontwikkelmenu tonen in menubalk&quot; in
* Het venster Voorkeuren sluiten

## Safari verbinden met iOS {#connect-safari-to-ios}

U kunt Safari verbinden met een iOS-apparaat of emulator.

* Navigeer in een consolevenster naar de hoofdmap van de uitgepakte bron.
* Voer de volgende opdracht in, zodat u de app op uw apparaat of emulator kunt starten.

```xml
phonegap run <platform> --device

// -- or -- //

phonegap run <platform> --emulator
```

* Safari openen
* Klik op Ontwikkelen in de menubalk
* Het submenu iOS Simulator selecteren
* Klik op home.html

![ chlimage_1-48 ](assets/chlimage_1-48.png)

## Fouten opsporen in JavaScript met Safari&#39;s webcontrole {#debug-javascript-with-safari-s-web-inspector}

U kunt onderbrekingspunten overal in de bron instellen. Wanneer u met uw emulator of apparaat werkt, stopt de uitvoering van uw app bij die onderbrekingspunten. U kunt de uitvoering doorlopen en de waarden in variabelen inspecteren.

* Klik Middelen in het venster van de Inspecteur van het Web
* Navigeren in de bronstructuur en op het gewenste bronbestand klikken
* Klik op het regelnummer naast een onderbrekingspunt
* Interactie met apparaat of emulator

![ chlimage_1-49 ](assets/chlimage_1-49.png)

* Gebruik de besturingsknoppen om door te gaan met de uitvoering, stap over, stap in en stap uit de methoden:

![ Vijf verschillende werkende die controleknopen in een horizontale rij worden gericht.](do-not-localize/chlimage_1-4.png)

>[!NOTE]
>
>Als u de waarden van variabelen in de huidige methode wilt zien, plaatst u de muis.

## De volgende stappen {#the-next-steps}

Nadat u over het Ontwikkelen van Apps met CLI PhoneGap hebt geleerd, zie [ Toegang tot de Eigenschappen van het Apparaat ](/help/mobile/phonegap-access-device-features.md).
