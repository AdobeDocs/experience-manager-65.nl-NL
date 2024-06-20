---
title: Aanpassing branding
description: Pas het toepassingspictogram, de toepassingsnaam, de lanceringsbeelden, en login pagina aan om een duidelijk organisatie-specifieke blik en een gevoel aan AEM Forms app te verstrekken.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 9333705b-9944-4a74-a30f-7d9ec85fd824
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 0%

---

# Aanpassing branding {#branding-customization}

U kunt het toepassingspictogram, de toepassingsnaam, lanceringsbeelden, en login pagina aanpassen om een duidelijk organisatie-specifieke verschijning aan AEM Forms app te verstrekken. U kunt de afbeeldingen bijvoorbeeld wijzigen en logo&#39;s van uw organisatie gebruiken. De AEM Forms-app ondersteunt de volgende aanpassingen:

* Het toepassingspictogram aanpassen en afbeeldingen starten
* Toepassingsnaam aanpassen
* Afbeeldingen op de aanmeldingspagina aanpassen
* Het logo aanpassen in het app-menu

## Pictogram aanpassen en afbeeldingen starten {#customizing-icon-and-launch-images}

Voer de volgende stappen uit om het standaardpictogram voor de app en de opstartafbeelding van de AEM Forms-app aan te passen:

>[!NOTE]
>
>Gebruik voor alle pictogrammen en afbeeldingen de niet-geïnterlinieerde PNG-indeling.

### Pictogram aanpassen en afbeeldingen starten {#to-customize-icon-and-launch-images}

#### Voor iOS {#for-ios}

1. Open de `Capture.xcodeproj` project in Xcode.
1. (***Pictogram voor aanpassen***) Navigeer in de navigatorweergave van Vastleggen naar **[!UICONTROL Capture > Capture > Supporting Files > Capture-info.plist]**. Klik op de vervolgkeuzelijst naast de pictogrambestanden. Geef de naam van het pictogrambestand (.png) op en upload het bestand op **[!UICONTROL Capture > Capture > Resources > icons]**. Ondersteunde afmetingen zijn: 29x29, 50x50, 58x58, 72x72, 100x100 en 144x144.
1. (***Startafbeeldingen aanpassen***) Zorg ervoor dat de bestandsnamen van de afbeeldingen als volgt zijn:

   * Voor staand: `Default-Portrait~ipad.png` en `Default-Portrait@2x~ipad.png`
   * Voor liggend: `Default-Landscape~ipad.png` en `Default-Landscape@2x~ipad.png`

   Upload hen aan het project van de Vangst om bestaande dossiers in het project te vervangen.

   >[!NOTE]
   >
   >Zorg ervoor dat de naam en resolutie van de afbeelding overeenkomen met de afbeelding die u in het project vervangt.

1. AEM Forms-app ontwikkelen en uitvoeren op iOS-apparaat of iOS-simulator.

#### Voor Android {#for-android}

1. Geef de pictogrambestanden van de toepassing een naam als:

   `ic_launcher.png`

1. Plaats de corresponderende pictogrambestanden in de volgende directory&#39;s:

   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-hdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-mdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-xhdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-xxhdpi`
   * `[User_Home]/Projects/[your-project]/src/android/res/drawable-xxxhdpi`

   >[!NOTE]
   >
   >Zorg ervoor dat de naam en resolutie van de afbeelding overeenkomen met de afbeelding die u in het project vervangt.

1. Maak de AEM Forms-app opnieuw.

### Voor Windows {#for-windows}

1. De pictogrammen in het pad vervangen:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\res\icons\windows`

1. Vervang de startafbeelding in het pad:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\res\screens\windows`

   >[!NOTE]
   >
   >Zorg ervoor dat de naam en resolutie van de afbeelding overeenkomen met de afbeelding die u in het project vervangt.

1. Maak de AEM Forms-app opnieuw.

## De toepassingsnaam aanpassen {#customize-the-app-name}

### Voor iOS {#for-ios-1}

1. Open de `Capture.xcodeproj` project in Xcode.
1. Navigeer in de navigatorweergave van Vastleggen naar **[!UICONTROL Capture > Capture > Supporting Files > InfoPlist.strings]**.

   Werk de waarde voor de `CFBundleDisplayName` aan een naam kenmerkt u voor app wilt tonen.

1. AEM Forms-app ontwikkelen en uitvoeren op iOS-apparaat of iOS-simulator.

   Ga voor meer informatie over het ontwikkelen van de app voor iOS naar [Het Xcode-project instellen en de iOS-app ontwikkelen](/help/forms/using/setup-xcode-project-build-installer.md).

### Voor Android {#for-android-1}

1. Open de volgende XML in om het even welke tekst of redacteur Xml:

   `[User_Home]/Projects/[your-project]/src/android/res/values/strings.xml and android/res/values-en/strings.xml`

1. De waarde voor de toets bijwerken `app_name`.
1. Maak de AEM Forms-app opnieuw.

   Ga voor meer informatie over het ontwikkelen van de app voor Android naar [Het Eclipse-project instellen en de Android-app ontwikkelen](/help/forms/using/setup-eclipse-project-build-installer.md).

### Voor Windows {#for-windows-1}

1. Open de volgende XML in om het even welke tekstredacteur:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\config.xml`

1. Werk de waarde in het dialoogvenster `<name>...</name>` -tag.
1. Maak de AEM Forms-app opnieuw.

   Ga voor meer informatie over het ontwikkelen van de app voor Windows naar [Opstelling het project van Visual Studio en bouwt Windows app](/help/forms/using/setup-visual-studio-project-build-installer.md).

## Afbeeldingen op de aanmeldingspagina aanpassen {#customizing-images-on-the-login-page}

De aanmeldingspagina van de AEM Forms-app bevat logo- en achtergrondafbeeldingen. Het logo bevindt zich boven het aanmeldingsvenster en de achtergrondafbeelding bevindt zich onder het aanmeldingsvenster. Voer de volgende stappen uit om de standaardafbeelding op de aanmeldingspagina aan te passen:

**Voordat u begint**

Zorg ervoor dat u de volgende afbeeldingen hebt:

<table>
 <tbody>
  <tr>
   <th><p>Beschrijving</p> </th>
   <th><p>Grootte</p> </th>
   <th><p>Bestandsnaam</p> </th>
  </tr>
  <tr>
   <td><p>Logo</p> </td>
   <td><p>72 x 72 pixels</p> </td>
   <td><p>LC-logo.png</p> </td>
  </tr>
  <tr>
   <td><p>Achtergrondafbeelding (staand)</p> </td>
   <td><p>1280 x 989 pixels</p> </td>
   <td><p>Landing_bg.jpeg</p> </td>
  </tr>
 </tbody>
</table>

**Afbeeldingen op de aanmeldingspagina aanpassen met Xcode**

1. Open de `Capture.xcodeproj` project in Xcode.

1. Ga naar de `www/wsmobile/images`map.
1. Als u het logo wilt wijzigen, vervangt u de standaardinstelling `LC-logo.png` bestand met de aangepaste `LC-logo.png` bestand.
1. Als u de achtergrond wilt wijzigen, vervangt u de standaardinstelling `Landing_bg.jpeg` bestand met de aangepaste `Landing_bg.jpeg`bestand.
1. AEM Forms-app ontwikkelen en uitvoeren op iOS-apparaat of iOS-simulator.

### Afbeeldingen op de aanmeldingspagina&#39;s aanpassen met Eclipse {#to-customize-images-on-the-login-pages-using-eclipse}

1. Open het Android-project in Eclipse.

1. Ga naar de `assets/www/wsmobile/images`map.
1. Als u het logo wilt wijzigen, vervangt u de standaardinstelling `LC-logo.png` bestand met de aangepaste `LC-logo.png` bestand.
1. Als u de achtergrond wilt wijzigen, vervangt u de standaardinstelling `Landing_bg.jpeg` bestand met de aangepaste `Landing_bg.jpeg`bestand.
1. AEM Forms-app ontwikkelen en uitvoeren op Android-apparaat.

### Om beelden op de login pagina&#39;s aan te passen gebruikend Visual Studio {#to-customize-images-on-the-login-pages-using-visual-studio}

1. Open de `MWSWindows.sln` project in Visual Studio.

1. Ga naar de `MWSWindows\www\wsmobile\images`map.
1. Als u het logo wilt wijzigen, vervangt u de standaardinstelling `LC-logo.png` bestand met de aangepaste `LC-logo.png` bestand.
1. Als u de achtergrond wilt wijzigen, vervangt u de standaardinstelling `Landing_bg.jpeg` bestand met de aangepaste `Landing_bg.jpeg`bestand.
1. AEM Forms-app ontwikkelen en uitvoeren op Windows-apparaat.

## Het logo aanpassen in het app-menu {#customizing_images_on_the_login_page-1}

Nadat u zich hebt aangemeld bij de AEM Forms-app en de menuknop hebt geselecteerd, ziet u het logo boven het menu. Voer de volgende stappen uit om het standaardlogo aan te passen:

**Voordat u begint**

Zorg ervoor dat u de volgende afbeelding hebt:

<table>
 <tbody>
  <tr>
   <th><p>Beschrijving</p> </th>
   <th><p>Grootte</p> </th>
   <th><p>Bestandsnaam</p> </th>
  </tr>
  <tr>
   <td><p>Logo</p> </td>
   <td><p>72 x 72 pixels</p> </td>
   <td><p>aem_icon.png</p> </td>
  </tr>
 </tbody>
</table>

**Afbeeldingen op de aanmeldingspagina aanpassen met Xcode**

1. Open de `Capture.xcodeproj` project in Xcode.

1. Ga naar de `www/wsmobile/images`map.
1. Als u het logo wilt wijzigen, vervangt u de standaardinstelling `aem_icon.png` bestand met de aangepaste `aem_icon.png` bestand.
1. AEM Forms-app ontwikkelen en uitvoeren op iOS-apparaat of iOS-simulator.

### Afbeeldingen op de aanmeldingspagina&#39;s aanpassen met Eclipse {#to-customize-images-on-the-login-pages-using-eclipse-1}

1. Open het Android-project in Eclipse.

1. Ga naar de `assets/www/wsmobile/images`map.
1. Als u het logo wilt wijzigen, vervangt u de standaardinstelling `aem_icon.png` bestand met de aangepaste `aem_icon.png` bestand.
1. AEM Forms-app ontwikkelen en uitvoeren op Android-apparaat.

### Om beelden op de login pagina&#39;s aan te passen gebruikend Visual Studio {#to-customize-images-on-the-login-pages-using-visual-studio-1}

1. Open de `MWSWindows.sln` project in Visual Studio.

1. Ga naar de `MWSWindows\www\wsmobile\images`map.
1. Als u het logo wilt wijzigen, vervangt u de standaardinstelling `aem_icon.png` bestand met de aangepaste `aem_icon.png` bestand.
1. AEM Forms-app ontwikkelen en uitvoeren op Windows-apparaat.
