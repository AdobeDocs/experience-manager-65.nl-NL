---
title: De Android-app voor AEM Forms ontwikkelen
seo-title: De Android-app voor AEM Forms ontwikkelen
description: Stappen om het Android Studio-project in te stellen en het .apk-bestand voor de AEM Forms-app voor Android te maken
seo-description: Stappen om het Android Studio-project in te stellen en het .apk-bestand voor de AEM Forms-app voor Android te maken
uuid: 2e140aaf-5be5-4d5d-9941-9d1f4bf2debd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: f5d6d9bd-4f36-4a4f-8008-15fb853a9219
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# De Android-app voor AEM Forms ontwikkelen {#build-the-aem-forms-android-app}

Voer de volgende stappen uit in de aanbevolen volgorde om de Android-app voor AEM Forms te maken.

1. [Download het pakket met AEM Forms App Source Code](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-header-277929160)
1. [Omgevingsvariabelen instellen](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-header-111803610)
1. [Standaard AEM Forms-app ontwikkelen](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-heading-0)

## Download het pakket met AEM Forms App Source Code {#download-android-zip}

AEM Forms App Source Code Package verwijst naar het `adobe-lc-mobileworkspace-src-<version>.zip` archief. Dit archief bevat de broncode die is vereist voor het maken van een aangepaste AEM Forms-app. Het archief wordt opgenomen in het `adobe-aemfd-forms-app-src-pkg-<version>.zip`pakket dat beschikbaar is voor de gedeelde pakketbestanden.

Voer de volgende stappen uit om het `adobe-aemfd-forms-app-src-pkg-<version>.zip` bestand te downloaden:

1. Meld u als beheerder aan bij de auteur-instantie van de [AEM-server](http://localhost:4502/) en open [pakketshare](http://localhost:4502/crx/packageshare). U hebt een Adobe-id nodig om u aan te melden bij het delen van het pakket.
1. Zoek in [AEM-pakketshare](http://localhost:4502/crx/packageshare/login.html)naar `adobe-aemfd-forms-app-src-pkg-<version>.zip`het pakket dat op uw besturingssysteem van toepassing is en klik op **Downloaden**. Lees en accepteer de licentieovereenkomst en klik op **OK**. Het downloaden begint. Nadat u het bestand hebt gedownload, staat het woord **Gedownload** naast het pakket.
1. Klik op **Gedownload** nadat het downloaden is voltooid. U wordt omgeleid naar pakketbeheer. Zoek in pakketbeheer naar het gedownloade pakket en klik op **Installeren**.
1. Als u het archief met broncodes wilt downloaden, opent u **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in uw browser. Het ZIP-bestand voor de Android-app wordt gedownload op uw apparaat.
1. Extraheer de inhoud van het ZIP-bestand naar een map op uw lokale bestandssysteem. Bijvoorbeeld *C:\&amp;lt;Folder Structure>\adobe-lc-mobileworkspace-src-2.4.20*

In de volgende afbeelding wordt de structuur van de `adobe-lc-mobileworkspace-src-<version>.zip\android`map weergegeven.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Omgevingsvariabelen instellen {#set-environment-variable-android}

Stel de volgende omgevingsvariabelen in voordat u het constructieproces voor de app AEM Forms start:

* Stel de omgevingsvariabele JAVA_HOME in op de locatie van de JDK-software op het lokale bestandssysteem. Bijvoorbeeld C:\Program Files\Java\jdk1.8.0_181
* Stel de omgevingsvariabele van het `ANDROID_SDK_ROOT` systeem in op de SDK-locatie voor Android. Bijvoorbeeld C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk
* Stel de omgevingsvariabele van het `Path` systeem zo in dat deze de locatie van de map met platformen en tools voor Android bevat. Bijvoorbeeld C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\platform-tools and C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\tools.

## Standaard AEM Forms-app ontwikkelen {#set-up-the-xcode-project}

Nadat u het bestand adobe-lc-mobileworkspace-src-&lt;version>.zip hebt opgeslagen in het lokale bestandssysteem en de omgevingsvariabelen hebt ingesteld, kunt u de standaard Android-app voor AEM-formulieren maken met een van de volgende opties:

* [AEM Forms-app ontwikkelen met Android Studio](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-header-1347434739)
* [.apk-bestand genereren met Android Studio](/help/forms/using/setup-eclipse-project-build-installer.md#main-pars-header-0)

### AEM Forms-app ontwikkelen met Android Studio {#using-android-studio}

Voer de volgende stappen uit om een app voor AEM-formulieren te maken met Android Studio:

1. Start de Android Studio-toepassing op uw computer.
1. Klik op **Een bestaand Android Studio-project** openen. Als het dialoogvenster voor het openen van een bestaand project niet automatisch wordt weergegeven, selecteert u **Bestand** > **Openen**.
1. Navigeer naar *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* in het lokale bestandssysteem en klik op **OK**.

   De optie **Android** wordt weergegeven in het linkerdeelvenster.

   ![android_folder_studio](assets/android_folder_studio.png)

1. Selecteer **android** in het linkerdeelvenster en klik op **Uitvoeren** > &#39;android&#39; **** uitvoeren.
1. Selecteer het Android-apparaat in het gedeelte Verbonden apparaten in het dialoogvenster Implementatiedoel selecteren en klik op OK.

   Nadat u de ontwikkelomgeving hebt gemaakt, kunt u nu aanpassingen op de app toepassen. Gebruik de volgende artikelen om de app aan te passen:

   * [Aanpassing branding](/help/forms/using/branding-customization.md)
   * [Aanpassing thema](/help/forms/using/theme-customization.md)
   * [Aanpassing van bewegingen](/help/forms/using/gesture-customization.md)
   Nadat u de juiste aanpassingen op uw app hebt toegepast, kunt u het .apk-bestand genereren voor distributie.

### .apk-bestand genereren met Android Studio {#generate-apk-android-studio}

Voer de volgende stappen uit om het .apk-bestand te genereren met Android Studio:

1. Start de Android Studio-toepassing op uw computer.
1. Selecteer **Een bestaand Android Studio-project** openen. Als het dialoogvenster voor het openen van een bestaand project niet automatisch wordt weergegeven, selecteert u **Bestand** > **Openen**.
1. Navigeer naar *adobe-lc-mobileworkspace-src-&lt;version>.zip/android* in het lokale bestandssysteem en klik op **OK**.

   De optie Android wordt weergegeven in het linkerdeelvenster.

1. Selecteer **Build** > **Build APK** om het .apk-bestand te genereren.

   Selecteer Optioneel **Samenstellen** > Ondertekende APK **** genereren om een [ondertekende versie](https://developer.android.com/studio/publish/app-signing) van het .apk-bestand te genereren.

## Android Debug Bridge gebruiken {#build-android-debug-bridge}

Nadat het .apk-bestand is gegenereerd, voert u de volgende opdracht uit om de toepassing op een Android-apparaat te installeren met de [Android Debug Bridge](https://developer.android.com/tools/help/adb.html).

**Windows-gebruikers:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**MAC-gebruikers:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
