---
title: De AEM Forms Android-app ontwikkelen
seo-title: De AEM Forms Android-app ontwikkelen
description: Stappen om het Android Studio-project in te stellen en het .apk-bestand voor de AEM Forms-app voor Android te maken
seo-description: Stappen om het Android Studio-project in te stellen en het .apk-bestand voor de AEM Forms-app voor Android te maken
uuid: 2e140aaf-5be5-4d5d-9941-9d1f4bf2debd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: f5d6d9bd-4f36-4a4f-8008-15fb853a9219
translation-type: tm+mt
source-git-commit: 1dfc8fa91d3e5ae8ca49cf1f3cb739b59feb18cf
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---


# De AEM Forms Android-app {#build-the-aem-forms-android-app} samenstellen

Voer de volgende stappen uit in de aanbevolen volgorde om de Android-app voor AEM Forms te maken.

1. [Het AEM Forms App Source Code-pakket downloaden](#download-android-zip)
1. [Omgevingsvariabelen instellen](#set-environment-variable-android)
1. [Standaard AEM Forms-app ontwikkelen](#set-up-the-xcode-project)

## Download het AEM Forms App Source Code Package {#download-android-zip}

AEM Forms App Source Code Package verwijst naar het archief `adobe-lc-mobileworkspace-src-<version>.zip`. Dit archief bevat de broncode die is vereist voor het maken van een aangepaste AEM Forms-app. Het archief wordt opgenomen in het `adobe-aemfd-forms-app-src-pkg-<version>.zip`pakket dat beschikbaar is op de Softwaredistributie.

Voer de volgende stappen uit om het `adobe-aemfd-forms-app-src-pkg-<version>.zip` dossier te downloaden:

1. Open [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Tik **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]**:
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]**.
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Tik op de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en tik **[!UICONTROL Download]**.
1. Open [Pakketbeheer](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik **[!UICONTROL Install]**.
1. Als u het archief met broncodes wilt downloaden, opent u **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in uw browser. Het ZIP-bestand voor de Android-app wordt gedownload op uw apparaat.
1. Extraheer de inhoud van het ZIP-bestand naar een map op uw lokale bestandssysteem. Bijvoorbeeld *C:\&lt;Folder Structure>\adobe-lc-mobileworkspace-src-2.4.20*

In de volgende afbeelding wordt de structuur van de map `adobe-lc-mobileworkspace-src-<version>.zip\android`weergegeven.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Omgevingsvariabelen {#set-environment-variable-android} instellen

Stel de volgende omgevingsvariabelen in voordat u het constructieproces voor de AEM Forms-app start:

* Stel de omgevingsvariabele JAVA_HOME in op de locatie van de JDK-software op het lokale bestandssysteem. Bijvoorbeeld C:\Program Files\Java\jdk1.8.0_181
* Stel de systeemomgevingsvariabele `ANDROID_SDK_ROOT` in op de SDK-locatie voor Android. Bijvoorbeeld C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk
* Stel de systeemomgevingsvariabele `Path` zo in dat deze de locatie van de platformhulpprogramma&#39;s en tools-map voor Android bevat. Bijvoorbeeld C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\platform-tools and C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\tools.

## Standaard AEM Forms-app {#set-up-the-xcode-project} maken

Nadat u het bestand adobe-lc-mobileworkspace-src-&lt;version>.zip hebt opgeslagen in het lokale bestandssysteem en de omgevingsvariabelen hebt ingesteld, kunt u de standaard AEM Forms Android-app ontwikkelen met een van de volgende opties:

* [AEM Forms-app ontwikkelen met Android Studio](#using-android-studio)
* [.apk-bestand genereren met Android Studio](#generate-apk-android-studio)

### AEM Forms-app ontwikkelen met Android Studio {#using-android-studio}

Voer de volgende stappen uit om een AEM Forms-app te maken met Android Studio:

1. Start de Android Studio-toepassing op uw computer.
1. Klik **Open een bestaand project van Android Studio**. Als het dialoogvenster voor het openen van een bestaand project niet automatisch wordt weergegeven, selecteert u **Bestand** > **Openen**.
1. Navigeer naar *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* op het lokale bestandssysteem en klik op **OK**.

   De optie **android** wordt weergegeven in het linkerdeelvenster.

   ![android_folder_studio](assets/android_folder_studio.png)

1. Selecteer **android** in het linkerdeelvenster en klik **Run** > **Run &#39;android&#39;**.
1. Selecteer het Android-apparaat in het gedeelte Verbonden apparaten in het dialoogvenster Implementatiedoel selecteren en klik op OK.

   Nadat u de ontwikkelomgeving hebt gemaakt, kunt u nu aanpassingen op de app toepassen. Gebruik de volgende artikelen om de app aan te passen:

   * [Aanpassing branding](/help/forms/using/branding-customization.md)
   * [Aanpassing thema](/help/forms/using/theme-customization.md)
   * [Aanpassing van bewegingen](/help/forms/using/gesture-customization.md)

   Nadat u de juiste aanpassingen op uw app hebt toegepast, kunt u het .apk-bestand genereren voor distributie.

### .apk-bestand genereren met Android Studio {#generate-apk-android-studio}

Voer de volgende stappen uit om het .apk-bestand te genereren met Android Studio:

1. Start de Android Studio-toepassing op uw computer.
1. Selecteer **Een bestaand Android Studio-project openen**. Als het dialoogvenster voor het openen van een bestaand project niet automatisch wordt weergegeven, selecteert u **Bestand** > **Openen**.
1. Navigeer naar *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* op het lokale bestandssysteem en klik op **OK**.

   De optie Android wordt weergegeven in het linkerdeelvenster.

1. Selecteer **Build** > **Build APK** om het .apk-bestand te genereren.

   Selecteer desgewenst **Build** > **Genereer ondertekende APK** om een [ondertekende versie](https://developer.android.com/studio/publish/app-signing) van het .apk-bestand te genereren.

## Android Debug Bridge gebruiken {#build-android-debug-bridge}

Nadat het .apk-bestand is gegenereerd, voert u de volgende opdracht uit om de toepassing op een Android-apparaat te installeren met de [Android Debug Bridge](https://developer.android.com/tools/help/adb.html).

**Windows-gebruikers:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**MAC-gebruikers:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
