---
title: Aanpassing branding
seo-title: Aanpassing branding
description: Pas het toepassingspictogram, de toepassingsnaam, de lanceringsbeelden, en login pagina aan om een duidelijk organisatie-specifieke blik en een gevoel aan de app van Vormen van AEM te verstrekken.
seo-description: Pas het toepassingspictogram, de toepassingsnaam, de lanceringsbeelden, en login pagina aan om een duidelijk organisatie-specifieke blik en een gevoel aan de app van Vormen van AEM te verstrekken.
uuid: fece0fa8-c417-45eb-93f1-a91b49835fa0
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: f6440a36-719a-4f89-b7db-1af918a3469a
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Aanpassing branding {#branding-customization}

U kunt het toepassingspictogram, de naam van de toepassing, opstartafbeeldingen en de aanmeldingspagina aanpassen om de app AEM Forms een specifieke organisatie te geven. U kunt de afbeeldingen bijvoorbeeld wijzigen en logo&#39;s van uw organisatie gebruiken. De app AEM Forms ondersteunt de volgende aanpassingen:

* Het toepassingspictogram aanpassen en afbeeldingen starten
* Toepassingsnaam aanpassen
* Afbeeldingen op de aanmeldingspagina aanpassen
* Het logo aanpassen in het app-menu

## Pictogram aanpassen en afbeeldingen starten {#customizing-icon-and-launch-images}

Voer de volgende stappen uit om het standaardpictogram voor de app en de opstartafbeelding van de app AEM Forms aan te passen:

>[!NOTE]
>
>Gebruik voor alle pictogrammen en afbeeldingen de niet-geïnterlinieerde PNG-indeling.

### Pictogram aanpassen en afbeeldingen starten {#to-customize-icon-and-launch-images}

#### Voor iOS {#for-ios}

1. Open het `Capture.xcodeproj` project in Xcode.
1. (***Voor het aanpassen van het pictogram***) Navigeer in de navigatorweergave van Vastleggen naar **[!UICONTROL Vastleggen > Vastleggen > Ondersteunende bestanden > Vastleggen-info.plist]**. Klik op de vervolgkeuzelijst naast de pictogrambestanden. Geef de naam van het pictogrambestand (.png) op en upload het bestand via **[!UICONTROL Vastleggen > Vastleggen > Bronnen > pictogrammen]**. Momenteel ondersteunde dimesies zijn: 29x29, 50x50, 58x58, 72x72, 100x100 en 144x144.
1. (***Voor het aanpassen van opstartafbeeldingen***) Zorg ervoor dat de bestandsnamen van uw afbeeldingen als volgt zijn:

   * Voor staand: `Default-Portrait~ipad.png` en `Default-Portrait@2x~ipad.png`
   * Voor liggend: `Default-Landscape~ipad.png` en `Default-Landscape@2x~ipad.png`
   Upload hen aan het project van de Vangst om bestaande dossiers in het project te vervangen.

   >[!NOTE]
   >
   >Zorg ervoor dat de naam en resolutie van de afbeelding overeenkomen met de afbeelding die u in het project vervangt.

1. Maak en voer de app AEM Forms uit op een iOS-apparaat of iOS-simulator.

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

1. Maak de app AEM Forms opnieuw.

### Voor Windows {#for-windows}

1. De pictogrammen in het pad vervangen:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\res\icons\windows`

1. Vervang de startafbeelding in het pad:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\res\screens\windows`

   >[!NOTE]
   >
   >Zorg ervoor dat de naam en resolutie van de afbeelding overeenkomen met de afbeelding die u in het project vervangt.

1. Maak de app AEM Forms opnieuw.

## De toepassingsnaam aanpassen {#customize-the-app-name}

### Voor iOS {#for-ios-1}

1. Open het `Capture.xcodeproj` project in Xcode.
1. Navigeer in de navigatorweergave van Vastleggen naar **[!UICONTROL Vastleggen > Vastleggen > Ondersteunende bestanden > InfoPlist.strings]**.

   Werk de waarde voor het `CFBundleDisplayName` kenmerk bij naar een naam die u voor de app wilt weergeven.

1. Maak en voer de app AEM Forms uit op een iOS-apparaat of iOS-simulator.

   Zie Het Xcode-project [instellen en de iOS-app](/help/forms/using/setup-xcode-project-build-installer.md)samenstellen voor meer informatie over het maken van de app voor iOS.

### Voor Android {#for-android-1}

1. Open de volgende XML in om het even welke tekst of redacteur Xml:

   `[User_Home]/Projects/[your-project]/src/android/res/values/strings.xml and android/res/values-en/strings.xml`

1. Werk de waarde voor de sleutel bij `app_name`.
1. Maak de app AEM Forms opnieuw.

   Zie Het Eclipse-project [instellen en de Android-app](/help/forms/using/setup-eclipse-project-build-installer.md)ontwikkelen voor meer informatie over het maken van de app voor Android.

### Voor Windows {#for-windows-1}

1. Open de volgende XML in om het even welke tekstredacteur:

   `%HOMEPATH%\adobe-lc-mobileworkspace-src-<version>\src\windows\MWSWindows\config.xml`

1. Werk de waarde in de `<name>...</name>` tag bij.
1. Maak de app AEM Forms opnieuw.

   Voor details bij de bouw van app voor Vensters, zie [Opstelling het project van Visual Studio en bouwt Vensters app](/help/forms/using/setup-visual-studio-project-build-installer.md).

## Afbeeldingen op de aanmeldingspagina aanpassen {#customizing-images-on-the-login-page}

De aanmeldingspagina van de app AEM Forms bevat logo- en achtergrondafbeeldingen. Het logo bevindt zich boven het aanmeldingsvenster en de achtergrondafbeelding bevindt zich onder het aanmeldingsvenster. Voer de volgende stappen uit om de standaardafbeelding op de aanmeldingspagina aan te passen:

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

1. Open het `Capture.xcodeproj` project in Xcode.

1. Navigate to the `www/wsmobile/images`folder.
1. Als u het logo wilt wijzigen, vervangt u het standaardbestand door het aangepaste `LC-logo.png` `LC-logo.png` bestand.
1. Als u de achtergrond wilt wijzigen, vervangt u het `Landing_bg.jpeg` standaardbestand door het aangepaste `Landing_bg.jpeg`bestand.
1. Maak en voer de app AEM Forms uit op een iOS-apparaat of iOS-simulator.

### Afbeeldingen op de aanmeldingspagina&#39;s aanpassen met Eclipse {#to-customize-images-on-the-login-pages-using-eclipse}

1. Open het Android-project in Eclipse.

1. Navigate to the `assets/www/wsmobile/images`folder.
1. Als u het logo wilt wijzigen, vervangt u het standaardbestand door het aangepaste `LC-logo.png` `LC-logo.png` bestand.
1. Als u de achtergrond wilt wijzigen, vervangt u het `Landing_bg.jpeg` standaardbestand door het aangepaste `Landing_bg.jpeg`bestand.
1. De app AEM Forms ontwikkelen en uitvoeren op Android-apparaten.

### Om beelden op de login pagina&#39;s aan te passen gebruikend Visual Studio {#to-customize-images-on-the-login-pages-using-visual-studio}

1. Open het `MWSWindows.sln` project in Visual Studio.

1. Navigate to the `MWSWindows\www\wsmobile\images`folder.
1. Als u het logo wilt wijzigen, vervangt u het standaardbestand door het aangepaste `LC-logo.png` `LC-logo.png` bestand.
1. Als u de achtergrond wilt wijzigen, vervangt u het `Landing_bg.jpeg` standaardbestand door het aangepaste `Landing_bg.jpeg`bestand.
1. Maak en voer de app AEM Forms op Windows-apparaat uit.

## Het logo aanpassen in het app-menu {#customizing_images_on_the_login_page-1}

Nadat u zich hebt aangemeld bij de app AEM Forms en op de menuknop hebt getikt, ziet u het logo boven het menu. Voer de volgende stappen uit om het standaardlogo aan te passen:

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

1. Open het `Capture.xcodeproj` project in Xcode.

1. Navigate to the `www/wsmobile/images`folder.
1. Als u het logo wilt wijzigen, vervangt u het standaardbestand door het aangepaste `aem_icon.png` `aem_icon.png` bestand.
1. Maak en voer de app AEM Forms uit op een iOS-apparaat of iOS-simulator.

### Afbeeldingen op de aanmeldingspagina&#39;s aanpassen met Eclipse {#to-customize-images-on-the-login-pages-using-eclipse-1}

1. Open het Android-project in Eclipse.

1. Navigate to the `assets/www/wsmobile/images`folder.
1. Als u het logo wilt wijzigen, vervangt u het standaardbestand door het aangepaste `aem_icon.png` `aem_icon.png` bestand.
1. De app AEM Forms ontwikkelen en uitvoeren op Android-apparaten.

### Om beelden op de login pagina&#39;s aan te passen gebruikend Visual Studio {#to-customize-images-on-the-login-pages-using-visual-studio-1}

1. Open het `MWSWindows.sln` project in Visual Studio.

1. Navigate to the `MWSWindows\www\wsmobile\images`folder.
1. Als u het logo wilt wijzigen, vervangt u het standaardbestand door het aangepaste `aem_icon.png` `aem_icon.png` bestand.
1. Maak en voer de app AEM Forms op Windows-apparaat uit.
