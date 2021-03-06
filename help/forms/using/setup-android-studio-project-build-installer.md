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
source-git-commit: 1dfc8fa91d3e5ae8ca49cf1f3cb739b59feb18cf
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# Stel het Android-studioproject in en maak de Android-app {#set-up-the-android-studio-project-and-build-the-android-app}

Dit artikel is bedoeld voor het maken van de AEM Forms App 6.3.1.1 en latere versies. Zie [Het Eclipse-project instellen en de Androidâ„¢-app](/help/forms/using/setup-eclipse-project-build-installer.md) samenstellen voor informatie over het maken van een app op basis van de broncode van de AEM Forms App 6.3.

AEM Forms biedt de volledige broncode van de AEM Forms-app. De bron bevat alle componenten om een aangepaste AEM Forms-app te maken. Het archief van de broncode, `adobe-lc-mobileworkspace-src-<version>.zip` is een deel van `adobe-aemfd-forms-app-src-pkg-<version>.zip` pakket op de Distributie van de Software.

Voer de volgende stappen uit om de AEM Forms-toepassingsbron op te halen:

1. Open [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Tik **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]**:
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]**.
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Tik op de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en tik **[!UICONTROL Download]**.
1. Open [Pakketbeheer](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik **[!UICONTROL Install]**.

In de volgende afbeelding wordt de geĂ«xtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip` weergegeven.

![GeĂ«xtraheerde inhoud van de gecomprimeerde Androidâ„¢-bron](assets/mws-content-1.png)

In de volgende afbeelding wordt de mapstructuur van de map `android`in de map `src`weergegeven.

![Directorystructuur van de android-map in src](assets/android-folder.png)

## Standaard AEM Forms-app {#set-up-the-xcode-project} maken

1. Voer de volgende stappen uit om een project in Androidâ„¢ Studio op te zetten en een ondertekeningsidentiteit te verstrekken:

   Meld u aan bij een computer waarop Androidâ„¢ Studio is geĂ¯nstalleerd en geconfigureerd.

1. Kopieer het gedownloade `adobe-lc-mobileworkspace-src-<version>.zip` archief naar:

   **Voor MAC-gebruikers**:  `[User_Home]/Projects`

   **Voor WindowsÂ®-gebruikers**:  `%HOMEPATH%\Projects`

   >[!NOTE]
   >
   >Voor WindowsÂ® is het raadzaam het android-project op de systeemschijf te houden.

1. Extraheer het archief in de volgende map:

   **Voor MAC-gebruikers**:  `[User_Home]/Projects/[your-project]`

   **Voor WindowsÂ®-gebruikers**:  `%HOMEPATH%\Projects\[your-project]`

   >[!NOTE]
   >
   >Het wordt aanbevolen dat u het geĂ«xtraheerde android-project in de systeemschijf bewaart voordat u het project importeert in Android Studio.

1. Start Androidâ„¢ Studio.

   **Voor MAC-gebruikers**: Werk het  `local.properties` bestand in de  `[User_Home]/Projects/[your-project]/android` map bij en wijs de  `sdk.dir` variabele naar de  `SDK` locatie op het bureaublad.

   **Voor WindowsÂ®-gebruikers**: Werk het  `local.properties` bestand in de  `%HOMEPATH%\Projects\[your-project]\android` map bij en wijs de  `sdk.dir` variabele naar de  `SDK` locatie op het bureaublad.

1. Klik **[!UICONTROL Finish]** om het project te bouwen.

   Het project is beschikbaar in de Ontdekkingsreiziger van het Project ADT.

   ![project verduisteren nadat de app is gemaakt](assets/eclipsebuildmws.png)

1. Selecteer **[!UICONTROL Import Project (Eclipse ADT, Gradle, Etc.)]** in Androidâ„¢ Studio.
1. In de projectontdekkingsreiziger, selecteer de wortelfolder van het project dat u in het **de tekstvakje van de Folder van de Wortel** wilt bouwen:

   **Voor Mac-gebruikers:** [User_Home]/Projecten/MobileWorkspace/src/android

   **Voor WindowsÂ®-gebruikers:** %HOMEPATH%\Projects\MobileWorkspace\src\android

1. Nadat het project is geĂ¯mporteerd, wordt een pop-upvenster weergegeven met de optie voor het bijwerken van de insteekmodule Androidâ„¢. Klik afhankelijk van uw vereiste op de juiste knop.

   ![dontherinnerdmeagainOpmerisproject](assets/dontremindmeagainforthisproject.png)

1. Na het maken van de gradle wordt het volgende scherm weergegeven. Sluit het desbetreffende apparaat of de emulator aan op het systeem en klik op **[!UICONTROL Run Androidâ„¢]**.

   ![gradleconsole](assets/gradleconsole.png)

1. Androidâ„¢ Studio geeft de aangesloten apparaten en beschikbare emulators weer. Selecteer het apparaat waarop u de toepassing wilt uitvoeren en klik dan **OK**.

   ![aangesloten apparaat](assets/connecteddevice.png)

Nadat u het project hebt gemaakt, kunt u de toepassing installeren met Androidâ„¢ Debug Bridge of Androidâ„¢ Studio.

### Androidâ„¢ Debug Bridge {#andriod-debug-bridge} gebruiken

U kunt de toepassing op een Androidâ„¢-apparaat installeren via [Androidâ„¢ Debug Bridge](https://developer.android.com/tools/help/adb.html) met de volgende opdracht:

**Voor MAC-gebruikers**:  `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`

**Voor WindowsÂ®-gebruikers**:  `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`
