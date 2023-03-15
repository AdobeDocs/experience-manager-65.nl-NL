---
title: Omgeving instellen voor AEM Forms-app
seo-title: Set up environment for AEM Forms app
description: Hardware, software en licenties voor het samenstellen en implementeren van de AEM Forms-app.
seo-description: Hardware, software, and licenses to build and deploy the AEM Forms app.
uuid: 4123a6b7-5766-476c-9afb-f57029b148ad
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: e6b01ade-7ea3-42a7-872d-cc35a3d2782a
docset: aem65
exl-id: 1d1f9db2-83cf-4612-ac8c-d2638c3bbaea
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Omgeving instellen voor AEM Forms-app{#set-up-environment-for-aem-forms-app}

U hebt de volgende hardware, software en licenties nodig om de AEM Forms-app te maken en te implementeren:

## Voor Windows-apparaten {#for-windows-devices}

* Microsoft Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools for Apache Cordova

## Voor iOS-apparaten {#for-ios-devices}

* Apple Mac met Intel-processor en Mac OS X 10.9.5 of hoger
* iOS SDK 8.4 of hoger
* Xcode-versie: Xcode 6.4 voor OS X of hoger
* Lidmaatschap van het iOS Developer Enterprise-programma
* Enterprise-certificaat voor de distributie van interne iOS-apps
* Apple iPad met iOS 8.4 of hoger

## Voor Android-apparaten {#for-android-devices}

* Android Development Toolkit (ADT-bundel) die kan worden gedownload van [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Als de omgeving is ingesteld op een MAC-systeem, moet ADT worden geïnstalleerd in de map Programma&#39;s.
* Als de ADT op een andere locatie op MAC is geïnstalleerd of als de omgeving op een Windows-systeem is ingesteld, moet het ADT SDK-pad worden bijgewerkt in `local.properties` bestand dat beschikbaar is in `src\android` map in het geëxtraheerde bronarchief `mobileworkspace-src.zip`. Wijs in dit bestand de `sdk.dir` variabele naar de ADT SDK-locatie op uw bureaublad.

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip bevat PhoneGap SDK 5.0. Controleer of PhoneGap SDK niet vooraf is geïnstalleerd.
