---
title: Omgeving instellen voor AEM Forms-app
description: Hardware, software en licenties voor het samenstellen en implementeren van de AEM Forms-app.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 1d1f9db2-83cf-4612-ac8c-d2638c3bbaea
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Omgeving instellen voor AEM Forms-app{#set-up-environment-for-aem-forms-app}

U hebt de volgende hardware, software en licenties nodig om de AEM Forms-app te maken en te implementeren:

## Voor Windows-apparaten {#for-windows-devices}

* Microsoft® Windows 10
* Microsoft® Visual Studio 2015
* Microsoft® Visual Studio Tools for Apache Cordova

## Voor iOS-apparaten {#for-ios-devices}

* Apple Mac van Intel met macOS X 10.9.5 of hoger
* iOS SDK 8.4 of hoger
* Xcode-versie: Xcode 6.4 voor OS X of hoger
* Lidmaatschap van het iOS Developer Enterprise-programma
* Enterprise-certificaat voor de distributie van interne iOS-apps
* Apple iPad met iOS 8.4 of hoger

## Voor Android™-apparaten {#for-android-devices}

* Toolkit van de Ontwikkeling Android™ (de bundel van ADT) die van [&#x200B; https://developer.android.com/studio &#x200B;](https://developer.android.com/studio) kan worden gedownload
* Als de omgeving is ingesteld op een Mac-systeem, moet ADT worden geïnstalleerd in de map Programma&#39;s.
* Als de ADT op een andere locatie op Mac is geïnstalleerd of als de omgeving op een Windows-systeem is ingesteld, moet het ADT SDK-pad worden bijgewerkt in het `local.properties` -bestand. Dit bestand is beschikbaar in de map `src\android` in het geëxtraheerde bronarchief `mobileworkspace-src.zip` . Wijs in dit bestand de variabele `sdk.dir` aan op de ADT SDK-locatie op uw bureaublad.

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip bevat PhoneGap SDK 5.0. Controleer of PhoneGap SDK niet vooraf is geïnstalleerd.
