---
title: Omgeving instellen voor de app AEM Forms
seo-title: Omgeving instellen voor de app AEM Forms
description: Hardware, software en licenties voor het samenstellen en implementeren van de AEM Forms-app.
seo-description: Hardware, software en licenties voor het samenstellen en implementeren van de AEM Forms-app.
uuid: 4123a6b7-5766-476c-9afb-f57029b148ad
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: e6b01ade-7ea3-42a7-872d-cc35a3d2782a
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Omgeving instellen voor de app AEM Forms{#set-up-environment-for-aem-forms-app}

U hebt de volgende hardware, software en licenties nodig om de app AEM Forms te maken en te implementeren:

## Voor Windows-apparaten {#for-windows-devices}

* Microsoft Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools for Apache Cordova

## Voor iOS-apparaten {#for-ios-devices}

* Op Intel gebaseerde Apple Mac met Mac OS X 10.9.5 of hoger
* iOS SDK 8.4 of hoger
* Xcode-versie: Xcode 6.4 voor OS X of hoger
* Lidmaatschap van het iOS Developer Enterprise-programma
* Enterprise-certificaat voor de distributie van interne iOS-apps
* Apple iPad met iOS 8.4 of hoger

## Voor Android-apparaten {#for-android-devices}

* Android Development Toolkit (ADT-bundel) die kan worden gedownload van [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html)
* Als het milieu opstelling op een systeem van MAC is, zou ADT in de omslag van Toepassingen moeten worden geïnstalleerd.
* Als ADT in een andere plaats op MAC geïnstalleerd is, of als het milieu opstelling op een systeem van Vensters is, moet de weg van ADT SDK in `local.properties` dossier worden bijgewerkt dat in `src\android` omslag in het gehaalde bronarchief beschikbaar is `mobileworkspace-src.zip`. Wijs in dit bestand de `sdk.dir` variabele naar de ADT SDK-locatie op uw bureaublad.

>[!NOTE]
>
>adobe-lc-mobileworkspace-src.zip bevat PhoneGap SDK 5.0. Controleer of PhoneGap SDK niet vooraf is geïnstalleerd.
