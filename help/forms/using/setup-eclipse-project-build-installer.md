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

1. [Het AEM Forms App Source Code-pakket downloaden](#download-android-zip)
1. [Omgevingsvariabelen instellen](#set-environment-variable-android)
1. [Een standaard AEM Forms-app ontwikkelen](#set-up-the-xcode-project)

## Het AEM Forms App Source Code-pakket downloaden {#download-android-zip}

AEM Forms App Source Code Package verwijst naar de `adobe-lc-mobileworkspace-src-<version>.zip` archief. Dit archief bevat de broncode die is vereist voor het maken van een aangepaste AEM Forms-app. Het archief wordt opgenomen in het `adobe-aemfd-forms-app-src-pkg-<version>.zip`op de Software Distribution beschikbaar.

Als u het dialoogvenster `adobe-aemfd-forms-app-src-pkg-<version>.zip` voert u de volgende stappen uit:

1. Openen [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteren **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de **[!UICONTROL Filters]** sectie:
   1. Selecteren **[!UICONTROL Forms]** van de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt ook de opdracht **[!UICONTROL Search Downloads]** om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem. Selecteer **[!UICONTROL Accept EULA Terms]** en selecteert u **[!UICONTROL Download]**.
1. Openen [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)  en klik op **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.
1. Als u het archief met broncodes wilt downloaden, opent u **https://&lt;server>:&lt;port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-&lt;version>.zip** in uw browser. Het ZIP-bestand voor de Android-app wordt gedownload op uw apparaat.
1. Extraheer de inhoud van het ZIP-bestand naar een map op uw lokale bestandssysteem. Bijvoorbeeld: *C:\&lt;folder structure=&quot;&quot;>\adobe-lc-mobileworkspace-src-2.4.20*

In de volgende afbeelding wordt de structuur van de `adobe-lc-mobileworkspace-src-<version>.zip\android`map.

![zip_android_folder_structure](assets/zip_android_folder_structure.png)

## Omgevingsvariabelen instellen {#set-environment-variable-android}

Stel de volgende omgevingsvariabelen in voordat u het constructieproces voor de AEM Forms-app start:

* Stel de omgevingsvariabele JAVA_HOME in op de locatie van de JDK-software op het lokale bestandssysteem. Bijvoorbeeld C:\Program Files\Java\jdk1.8.0_181
* Stel de `ANDROID_SDK_ROOT` systeemomgevingsvariabele naar de SDK-locatie voor Android. Bijvoorbeeld C:\Users\&amp;lt;gebruikersnaam>\AppData\Local\Android\Sdk
* Stel de `Path` systeemomgevingsvariabele om de locatie van de platformhulpprogramma&#39;s en tools-map voor Android op te nemen. Bijvoorbeeld C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\platform-tools en C:\Users\&amp;lt;username>\AppData\Local\Android\Sdk\tools.

## Een standaard AEM Forms-app ontwikkelen {#set-up-the-xcode-project}

Nadat u de adobe-lc-mobileworkspace-src-&lt;version>.zip-bestand op het lokale bestandssysteem en stel de omgevingsvariabelen in, maak een standaard AEM Forms Android-app met een van de volgende opties:

* [AEM Forms-app ontwikkelen met Android Studio](#using-android-studio)
* [.apk-bestand genereren met Android Studio](#generate-apk-android-studio)

### AEM Forms-app ontwikkelen met Android Studio {#using-android-studio}

Voer de volgende stappen uit om een AEM Forms-app te maken met Android Studio:

1. Start de Android Studio-toepassing op uw computer.
1. Klikken **Een bestaand Android Studio-project openen**. Als het dialoogvenster voor het openen van een bestaand project niet automatisch wordt weergegeven, selecteert u **Bestand** > **Openen**.
1. Navigeren naar *adobe-lc-mobileworkspace-src&lt;version>.zip/android* op het lokale bestandssysteem en klik op **OK**.

   De **androïde** wordt weergegeven in het linkerdeelvenster.

   ![android_folder_studio](assets/android_folder_studio.png)

1. Selecteren **androïde** in het linkerdeelvenster en klik op **Uitvoeren** > **&#39;android&#39; uitvoeren**.
1. Selecteer het Android-apparaat in het gedeelte Verbonden apparaten in het dialoogvenster Implementatiedoel selecteren en klik op OK.

   Nadat u de ontwikkelomgeving hebt gemaakt, kunt u nu aanpassingen op de app toepassen. Gebruik de volgende artikelen om de app aan te passen:

   * [Aanpassing branding](/help/forms/using/branding-customization.md)
   * [Aanpassing thema](/help/forms/using/theme-customization.md)
   * [Aanpassing van bewegingen](/help/forms/using/gesture-customization.md)

   Nadat u de juiste aanpassingen op uw app hebt toegepast, kunt u het .apk-bestand genereren voor distributie.

### .apk-bestand genereren met Android Studio {#generate-apk-android-studio}

Ga als volgt te werk om het .apk-bestand te genereren met Android Studio:

1. Start de Android Studio-toepassing op uw computer.
1. Selecteren **Een bestaand Android Studio-project openen**. Als het dialoogvenster voor het openen van een bestaand project niet automatisch wordt weergegeven, selecteert u **Bestand** > **Openen**.
1. Navigeren naar *adobe-lc-mobileworkspace-src&lt;version>.zip/android* op het lokale bestandssysteem en klik op **OK**.

   De optie Android wordt weergegeven in het linkerdeelvenster.

1. Selecteer **Opbouwen** > **APK samenstellen**.

   Selecteer optioneel **Opbouwen** > **Ondertekende APK genereren** om een [ondertekende versie](https://developer.android.com/studio/publish/app-signing) van het .apk-bestand.

## Android Debug Bridge gebruiken {#build-android-debug-bridge}

Nadat het .apk-bestand is gegenereerd, voert u de volgende opdracht uit om de toepassing op een Android-apparaat te installeren met de opdracht [Android Debug Bridge](https://developer.android.com/tools/adb).

**Windows-gebruikers:** `adb install %HOMEPATH%\Projects\[your-project]\adobe-lc-mobileworkspace-src-[version]\android\build\outputs\apk\android-debug.apk`

**Mac-gebruikers:** `adb install [User_Home]/Projects/[your-project]/adobe-lc-mobileworkspace-src-[version]/android/build/outputs/apk/android-debug.apk`
