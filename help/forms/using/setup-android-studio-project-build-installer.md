---
title: Android&amp instellen;trade; studio-project en Android&amp bouwen;trade; app
description: Stappen voor het instellen van de Android&trade; Studio-project en het installatieprogramma voor de Adobe Experience Manager (AEM) Forms-app
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: forms-app
exl-id: 47d6af00-34d8-4e5d-8117-86fc1b6f58cb
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# Android™-studioproject instellen en de Android™-app ontwikkelen {#set-up-the-android-studio-project-and-build-the-android-app}

Dit artikel is bedoeld voor het maken van de AEM Forms App 6.3.1.1 en latere versies. Voor de bouw van een app van broncode van AEM Forms App 6.3, zie [&#x200B; Opstelling het project van de Verduistering en bouwt Android™ app &#x200B;](/help/forms/using/setup-eclipse-project-build-installer.md).

AEM Forms geeft de volledige broncode van de AEM Forms-app op. De bron bevat alle componenten om een aangepaste AEM Forms-app te maken. Het broncodearchief, `adobe-lc-mobileworkspace-src-<version>.zip` , maakt deel uit van het `adobe-aemfd-forms-app-src-pkg-<version>.zip` -pakket voor softwaredistributie.

Voer de volgende stappen uit om de AEM Forms-toepassingsbron op te halen:

1. Open [&#x200B; Distributie van de Software &#x200B;](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [&#x200B; Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=nl-NL) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip` weergegeven.

![&#x200B; Geëxtraheerde inhoud van de gecomprimeerde bron Android™ &#x200B;](assets/mws-content-1.png)

Het volgende beeld toont de folderstructuur van de `android` omslag in de `src` omslag.

![&#x200B; structuur van de Folder van de android omslag in src &#x200B;](assets/android-folder.png)

## Standaard AEM Forms-app ontwikkelen {#set-up-the-xcode-project}

1. Voer de volgende stappen uit om een project in Android™ Studio op te zetten en een het ondertekenen identiteit te verstrekken:

   Meld u aan bij een computer waarop Android™ Studio is geïnstalleerd en geconfigureerd.

1. Het gedownloade `adobe-lc-mobileworkspace-src-<version>.zip` archief kopiëren naar:

   **voor de gebruikers van Mac**: `[User_Home]/Projects`

   **voor gebruikers Windows®**: `%HOMEPATH%\Projects`

   >[!NOTE]
   >
   >Voor Windows® is het raadzaam het Android™-project op de systeemschijf te houden.

1. Extraheer het archief in de volgende map:

   **voor de gebruikers van Mac**: `[User_Home]/Projects/[your-project]`

   **voor gebruikers Windows®**: `%HOMEPATH%\Projects\[your-project]`

   >[!NOTE]
   >
   >U wordt aangeraden het geëxtraheerde Android-project op de systeemschijf te houden voordat u het project importeert in Android™ Studio.

1. Start Android™ Studio.

   **voor de gebruikers van Mac**: Werk het `local.properties` dossier in de `[User_Home]/Projects/[your-project]/android` omslag voor en richt de `sdk.dir` variabele aan `SDK` plaats op uw Desktop.

   **voor gebruikers Windows®**: Werk het `local.properties` dossier huidig in de `%HOMEPATH%\Projects\[your-project]\android` omslag bij en richt de `sdk.dir` variabele aan `SDK` plaats op uw Desktop.

1. Klik op **[!UICONTROL Finish]** om het project samen te stellen.

   Het project is beschikbaar in de Ontdekkingsreiziger van het Project ADT.

   ![&#x200B; eclipse project na de bouw app &#x200B;](assets/eclipsebuildmws.png)

1. Selecteer **[!UICONTROL Import Project (Eclipse ADT, Gradle, Etc.)]** in Android™ Studio.
1. In de projectontdekkingsreiziger, selecteer de wortelfolder van het project dat u in het **de tekstvakje van de Folder van de 1&rbrace; wortel wilt bouwen**:

   **voor de gebruikers van Mac:** [ User_Home ]/Projecten/MobileWorkspace/src/android

   **voor gebruikers Windows®:** %HOMEPATH%\Projects\MobileWorkspace\src\android

1. Nadat het project is geïmporteerd, wordt een pop-upvenster weergegeven met de optie voor het bijwerken van de Android™-insteekmodule Gradle. Klik afhankelijk van uw vereiste op de juiste knop.

   ![&#x200B; dontherinnerdmeagainopenisproject &#x200B;](assets/dontremindmeagainforthisproject.png)

1. Na het maken van de gradle wordt het volgende scherm weergegeven. Sluit het desbetreffende apparaat of de emulator aan op het systeem en klik op **[!UICONTROL Run Android™]** .

   ![&#x200B; gradleconsole &#x200B;](assets/gradleconsole.png)

1. Android™ Studio geeft de aangesloten apparaten en beschikbare emulators weer. Selecteer het apparaat waarop u de toepassing wilt in werking stellen en dan **O.K.** klikken.

   ![&#x200B; verbonden apparaat &#x200B;](assets/connecteddevice.png)

Nadat u het project hebt gemaakt, kunt u de toepassing installeren met Android™ Debug Bridge of Android™ Studio.

### Android™ Debug Bridge gebruiken {#andriod-debug-bridge}

U kunt de toepassing op een Android™ apparaat als [&#x200B; Android™ installeren zuivert Bridge &#x200B;](https://developer.android.com/tools/adb) met het volgende bevel:

**voor de gebruikers van Mac**: `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`

**voor gebruikers Windows®**: `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`
