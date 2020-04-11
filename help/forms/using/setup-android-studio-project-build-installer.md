---
title: Het Android-studioproject instellen en de Android-app ontwikkelen
seo-title: Het Android-studioproject instellen en de Android-app ontwikkelen
description: Stappen om het Android Studio-project in te stellen en het installatieprogramma voor de AEM Forms-app te maken
seo-description: Stappen om het Android Studio-project in te stellen en het installatieprogramma voor de AEM Forms-app te maken
uuid: 4c966cdc-d0f5-4b5b-b21f-f11e8a35ec8a
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: forms-app
discoiquuid: fabc981e-0c9e-4157-b0a1-0c13717fb6cd
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Het Android-studioproject instellen en de Android-app ontwikkelen {#set-up-the-android-studio-project-and-build-the-android-app}

Dit artikel is bedoeld voor het samenstellen van de AEM Forms App 6.3.1.1 en latere versies. Zie Het Eclipse-project [instellen en de Android™-app](/help/forms/using/setup-eclipse-project-build-installer.md)ontwikkelen voor informatie over het ontwikkelen van een app op basis van broncode in AEM Forms App 6.3.

AEM Forms bevat de volledige broncode van de app AEM Forms. De bron bevat alle componenten om een aangepaste AEM Forms-app te maken. Het broncodearchief `adobe-lc-mobileworkspace-src-<version>.zip` maakt deel uit van het `adobe-aemfd-forms-app-src-pkg-<version>.zip` pakket voor delen van pakketten.

Voer de volgende stappen uit om de App-bron van AEM Forms te verkrijgen:

1. Navigeren naar delen pakket

   URL: `https://<server>:<port>/crx/packageshare`.

1. Download het bronpakket. Wanneer u het pakket downloadt, wordt het toegevoegd in het pakketbeheer van AEM Forms.
1. Ga na het downloaden naar: `https://<server>:<port>/crx/packmgr/index.jsp`, en installeer `adobe-aemfd-forms-app-src-pkg-<version>.zip`.

1. Als u het archief met broncodes wilt downloaden, opent u `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` de browser.

   Het bronpakket wordt gedownload op uw apparaat.

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip`afbeelding weergegeven.

![Geëxtraheerde inhoud van de gecomprimeerde Android™-bron](assets/mws-content-1.png)

In de volgende afbeelding wordt de mapstructuur van de `android`map in de `src`map weergegeven.

![Directorystructuur van de android-map in src](assets/android-folder.png)

## Standaard AEM Forms-app ontwikkelen {#set-up-the-xcode-project}

1. Voer de volgende stappen uit om een project in Android™ Studio op te zetten en een ondertekeningsidentiteit te verstrekken:

   Meld u aan bij een computer waarop Android™ Studio is geïnstalleerd en geconfigureerd.

1. Het gedownloade `adobe-lc-mobileworkspace-src-<version>.zip` archief kopiëren naar:

   **Voor MAC-gebruikers**: `[User_Home]/Projects`

   **Voor Windows®-gebruikers**: `%HOMEPATH%\Projects`

   >[!NOTE]
   >
   >Voor Windows® is het raadzaam het android-project op de systeemschijf te houden.

1. Extraheer het archief in de volgende map:

   **Voor MAC-gebruikers**: `[User_Home]/Projects/[your-project]`

   **Voor Windows®-gebruikers**: `%HOMEPATH%\Projects\[your-project]`

   >[!NOTE]
   >
   >Het wordt aanbevolen dat u het geëxtraheerde android-project in de systeemschijf bewaart voordat u het project importeert in Android Studio.

1. Start Android™ Studio.

   **Voor MAC-gebruikers**: Werk het `local.properties` bestand in de `[User_Home]/Projects/[your-project]/android` map bij en wijs de `sdk.dir` variabele naar de `SDK` locatie op het bureaublad.

   **Voor Windows®-gebruikers**: Werk het `local.properties` bestand in de `%HOMEPATH%\Projects\[your-project]\android` map bij en wijs de `sdk.dir` variabele naar de `SDK` locatie op het bureaublad.

1. Klik op **[!UICONTROL Voltooien]** om het project samen te stellen.

   Het project is beschikbaar in de Ontdekkingsreiziger van het Project ADT.

   ![project verduisteren nadat de app is gemaakt](assets/eclipsebuildmws.png)

1. Selecteer Project **[!UICONTROL importeren (Eclipse ADT, Gradle, enz.)]** in Android™ Studio.
1. In de projectverkenner, selecteer de wortelfolder van het project dat u in het de tekstvakje van de Folder van de **Wortel** wilt bouwen:

   **Voor Mac-gebruikers:** [User_Home]/projects/MobileWorkspace/src/android

   **Voor Windows®-gebruikers:** %HOMEPATH%\Projects\MobileWorkspace\src\android

1. Nadat het project is geïmporteerd, wordt een pop-upvenster weergegeven met de optie voor het bijwerken van de insteekmodule Android™. Klik afhankelijk van uw vereiste op de juiste knop.

   ![dontherinnerdmeagainOpmerisproject](assets/dontremindmeagainforthisproject.png)

1. Na het maken van de gradle wordt het volgende scherm weergegeven. Sluit het desbetreffende apparaat of de emulator aan op het systeem en klik op **[!UICONTROL Android™]** uitvoeren.

   ![gradleconsole](assets/gradleconsole.png)

1. Android™ Studio geeft de aangesloten apparaten en beschikbare emulators weer. Selecteer het apparaat waarop u de toepassing wilt uitvoeren en klik op **OK**.

   ![aangesloten apparaat](assets/connecteddevice.png)

Nadat u het project hebt gemaakt, kunt u de toepassing installeren met Android™ Debug Bridge of Android™ Studio.

### Android™ Debug Bridge gebruiken {#andriod-debug-bridge}

U kunt de toepassing op een Android™-apparaat installeren via [Android™ Debug Bridge](https://developer.android.com/tools/help/adb.html) met de volgende opdracht:

**Voor MAC-gebruikers**: `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`

**Voor Windows®-gebruikers**: `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`
