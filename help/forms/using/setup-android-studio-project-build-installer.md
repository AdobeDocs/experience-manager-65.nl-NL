---
title: Android&trade instellen; studio-project en Android&trade ontwikkelen; app
description: Stappen voor het instellen van Android&trade; Studio-project en het installatieprogramma voor de Adobe Experience Manager (AEM) Forms-app
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: forms-app
exl-id: 47d6af00-34d8-4e5d-8117-86fc1b6f58cb
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# Het Android™-studioproject instellen en de Android™-app ontwikkelen {#set-up-the-android-studio-project-and-build-the-android-app}

Dit artikel is bedoeld voor het maken van de AEM Forms App 6.3.1.1 en latere versies. Voor het maken van een app op basis van de broncode van de AEM Forms App 6.3 raadpleegt u [Het Eclipse-project instellen en de Android™-app ontwikkelen](/help/forms/using/setup-eclipse-project-build-installer.md).

AEM Forms geeft de volledige broncode van de AEM Forms-app op. De bron bevat alle componenten om een aangepaste AEM Forms-app te maken. Het broncodearchief, `adobe-lc-mobileworkspace-src-<version>.zip` maakt deel uit van de `adobe-aemfd-forms-app-src-pkg-<version>.zip` pakket over Softwaredistributie.

Voer de volgende stappen uit om de AEM Forms-toepassingsbron op te halen:

1. Openen [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteren **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de **[!UICONTROL Filters]** sectie:
   1. Selecteren **[!UICONTROL Forms]** van de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt ook de opdracht **[!UICONTROL Search Downloads]** om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem. Selecteer **[!UICONTROL Accept EULA Terms]** en selecteert u **[!UICONTROL Download]**.
1. Openen [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)  en klik op **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip`.

![Inhoud van de gecomprimeerde Android™-bron extraheren](assets/mws-content-1.png)

In de volgende afbeelding wordt de mapstructuur van de `android`in de `src`map.

![Directorystructuur van de android-map in src](assets/android-folder.png)

## Standaard AEM Forms-app ontwikkelen {#set-up-the-xcode-project}

1. Voer de volgende stappen uit om een project in Android™ Studio op te zetten en een ondertekeningsidentiteit te verstrekken:

   Meld u aan bij een computer waarop Android™ Studio is geïnstalleerd en geconfigureerd.

1. Het gedownloade bestand kopiëren `adobe-lc-mobileworkspace-src-<version>.zip` archiveren tot:

   **Voor Mac-gebruikers**: `[User_Home]/Projects`

   **Voor Windows®-gebruikers**: `%HOMEPATH%\Projects`

   >[!NOTE]
   >
   >Voor Windows® is het raadzaam het Android™-project op de systeemschijf te houden.

1. Extraheer het archief in de volgende map:

   **Voor Mac-gebruikers**: `[User_Home]/Projects/[your-project]`

   **Voor Windows®-gebruikers**: `%HOMEPATH%\Projects\[your-project]`

   >[!NOTE]
   >
   >U wordt aangeraden het geëxtraheerde Android-project op de systeemschijf te houden voordat u het project importeert in Android™ Studio.

1. Start Android™ Studio.

   **Voor Mac-gebruikers**: Werk de `local.properties` bestand aanwezig in `[User_Home]/Projects/[your-project]/android` map en wijs de `sdk.dir` variabele tot `SDK` locatie op uw bureaublad.

   **Voor Windows®-gebruikers**: Werk de `local.properties` bestand aanwezig in `%HOMEPATH%\Projects\[your-project]\android` map en wijs de `sdk.dir` variabele tot `SDK` locatie op uw bureaublad.

1. Klikken **[!UICONTROL Finish]** om het project te bouwen.

   Het project is beschikbaar in de Ontdekkingsreiziger van het Project ADT.

   ![project verduisteren nadat de app is gemaakt](assets/eclipsebuildmws.png)

1. Selecteer in Android™ Studio **[!UICONTROL Import Project (Eclipse ADT, Gradle, Etc.)]**.
1. In de projectverkenner, selecteer de wortelfolder van het project dat u in wilt bouwen **Hoofdmap** tekstvak:

   **Voor Mac-gebruikers:** [Gebruiker_startpunt]/Projecten/MobileWorkspace/src/android

   **Voor Windows®-gebruikers:** %HOMEPATH%\Projects\MobileWorkspace\src\android

1. Nadat het project is geïmporteerd, wordt een pop-upvenster weergegeven met de optie voor het bijwerken van de insteekmodule Android™. Klik afhankelijk van uw vereiste op de juiste knop.

   ![dontherinnerdmeagainOpmerisproject](assets/dontremindmeagainforthisproject.png)

1. Na het maken van de gradle wordt het volgende scherm weergegeven. Sluit het desbetreffende apparaat of de emulator aan op het systeem en klik op **[!UICONTROL Run Android™]**.

   ![gradleconsole](assets/gradleconsole.png)

1. Android™ Studio geeft de aangesloten apparaten en beschikbare emulators weer. Selecteer het apparaat waarop u de toepassing wilt uitvoeren en klik vervolgens op **OK**.

   ![aangesloten apparaat](assets/connecteddevice.png)

Nadat u het project hebt gemaakt, kunt u de toepassing installeren met Android™ Debug Bridge of Android™ Studio.

### Android™ Debug Bridge gebruiken {#andriod-debug-bridge}

U kunt de toepassing via de [Android™ Debug Bridge](https://developer.android.com/tools/adb) met de volgende opdracht:

**Voor Mac-gebruikers**: `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`

**Voor Windows®-gebruikers**: `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`
