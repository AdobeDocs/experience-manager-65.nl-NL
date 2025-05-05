---
title: De AEM Forms Android-app ontwikkelen
description: Stappen om het Android Studio-project in te stellen en het .apk-bestand voor de AEM Forms-app voor Android te maken
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 3fb069cf-d3ed-47b0-b6bf-82e110b3b059
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---

# De AEM Forms Android-app ontwikkelen {#build-the-aem-forms-android-app}

Voer de volgende stappen uit in de aanbevolen volgorde om de Android-app voor AEM Forms te maken.

1. [Het AEM Forms App Source-codepakket downloaden](#download-android-zip)
1. [Omgevingsvariabelen instellen](#set-environment-variable-android)
1. [Een standaard AEM Forms-app ontwikkelen](#set-up-the-xcode-project)

## Het AEM Forms App Source-codepakket downloaden {#download-android-zip}

AEM Forms App Source Code Package verwijst naar het `adobe-lc-mobileworkspace-src-<version>.zip` archief. Dit archief bevat de broncode die is vereist voor het maken van een aangepaste AEM Forms-app. Het archief is inbegrepen in het `adobe-aemfd-forms-app-src-pkg-<version>.zip` pakket beschikbaar op de Distributie van de Software.

Voer de volgende stappen uit om het `adobe-aemfd-forms-app-src-pkg-<version>.zip` -bestand te downloaden:

1. Open [ Distributie van de Software ](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=nl-NL) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]** .
1. Om het bron-code archief te downloaden, open **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in uw browser. Het .zip-bestand van de Android-app wordt gedownload naar uw apparaat.
1. Extraheer de inhoud van het ZIP-bestand naar een map op uw lokale bestandssysteem. Bijvoorbeeld, *C:\&lt;Folder Structure> \ adobe-lc-mobileworkspace-src-2.4.20*

Het volgende beeld toont de structuur van de `adobe-lc-mobileworkspace-src-<version>.zip\android` omslag.

![ zip_android_folder_structure ](assets/zip_android_folder_structure.png)

## Omgevingsvariabelen instellen {#set-environment-variable-android}

Stel de volgende omgevingsvariabelen in voordat u het constructieproces voor de AEM Forms-app start:

* Stel de omgevingsvariabele JAVA_HOME in op de locatie van de JDK-software op het lokale bestandssysteem. Bijvoorbeeld C:\Program Files\Java\jdk1.8.0_181
* Stel de systeemomgevingsvariabele `ANDROID_SDK_ROOT` in op de SDK-locatie voor Android. Bijvoorbeeld C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk
* Stel de systeemomgevingsvariabele `Path` zo in dat deze de locatie van de platformgereedschappen en tools-map voor Android bevat. Bijvoorbeeld C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\platform-tools en C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\tools.

## Een standaard AEM Forms-app ontwikkelen {#set-up-the-xcode-project}

Nadat u het bestand adobe-lc-mobileworkspace-src-&lt;version>.zip hebt opgeslagen in het lokale bestandssysteem en de omgevingsvariabelen hebt ingesteld, maakt u een standaard AEM Forms Android-app met een van de volgende opties:

* [AEM Forms-app ontwikkelen met Android Studio](#using-android-studio)
* [.apk-bestand genereren met Android Studio](#generate-apk-android-studio)

### AEM Forms-app ontwikkelen met Android Studio {#using-android-studio}

Voer de volgende stappen uit om een AEM Forms-app te maken met Android Studio:

1. Start de Android Studio-toepassing op uw computer.
1. Klik **Open een bestaand project van Android Studio**. Als de dialoogdoos om een bestaand project te openen niet automatisch verschijnt, uitgezochte **Dossier** > **Open**.
1. Navigeer aan *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* op het lokale dossiersysteem en klik **O.K.**.

   De **android** optie wordt getoond in de linkerruit.

   ![ android_folder_studio ](assets/android_folder_studio.png)

1. Selecteer **android** van de linkerruit en klik **Looppas** > **Looppas &quot;android&quot;**.
1. Selecteer het Android-apparaat in de sectie Connected Devices in het dialoogvenster Select Deployment Target (Doel voor implementatie selecteren) en klik op OK.

   Nadat u de ontwikkelomgeving hebt gemaakt, kunt u nu aanpassingen op de app toepassen. Gebruik de volgende artikelen om de app aan te passen:

   * [Aanpassing branding](/help/forms/using/branding-customization.md)
   * [Aanpassing thema](/help/forms/using/theme-customization.md)
   * [Aanpassing van bewegingen](/help/forms/using/gesture-customization.md)

   Nadat u de juiste aanpassingen op uw app hebt toegepast, kunt u het .apk-bestand genereren voor distributie.

### .apk-bestand genereren met Android Studio {#generate-apk-android-studio}

Ga als volgt te werk om het .apk-bestand te genereren met Android Studio:

1. Start de Android Studio-toepassing op uw computer.
1. Selecteer **Open een bestaand project van Android Studio**. Als de dialoogdoos om een bestaand project te openen niet automatisch verschijnt, uitgezochte **Dossier** > **Open**.
1. Navigeer aan *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* op het lokale dossiersysteem en klik **O.K.**.

   De optie Android wordt weergegeven in het linkerdeelvenster.

1. Om het .apk dossier te produceren, uitgezochte **bouwt** > **APK** bouwt.

   Naar keuze, selecteer **Bouwstijl** > **Genereer Ondertekende APK** om a [ ondertekende versie ](https://developer.android.com/studio/publish/app-signing) van het .apk dossier te produceren.

## Android Debug Bridge gebruiken {#build-android-debug-bridge}

Zodra het .apk dossier is geproduceerd, voer het volgende bevel uit om de toepassing op een apparaat van Android te installeren gebruikend [ Android zuivert Bridge ](https://developer.android.com/tools/adb).

**gebruikers van Vensters:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**de gebruikers van Mac:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
