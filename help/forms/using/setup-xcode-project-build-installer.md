---
title: Het Xcode-project instellen en de iOS-app ontwikkelen
seo-title: Het Xcode-project instellen en de iOS-app ontwikkelen
description: Hierin wordt uitgelegd hoe u een standaard AEM Forms-app voor iOS kunt maken.
seo-description: Hierin wordt uitgelegd hoe u een standaard AEM Forms-app voor iOS kunt maken.
uuid: 29779bbb-06b4-4ece-9f29-786afab59eaf
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 88555db2-712f-4ef9-bf47-76c7ba83d964
docset: aem65
translation-type: tm+mt
source-git-commit: 72a582b7ac19322b81fd1a92de8fce34e55b9db1

---


# Het Xcode-project instellen en de iOS-app ontwikkelen{#set-up-the-xcode-project-and-build-the-ios-app}

AEM Forms bevat de volledige broncode van de app AEM Forms. De bron bevat alle componenten om een aangepaste app voor AEM-formulieren te maken. Het broncodearchief `adobe-lc-mobileworkspace-src-<version>.zip` maakt deel uit van het `adobe-aemfd-forms-app-src-pkg-<version>.zip` pakket voor delen van pakketten.

Voer de volgende stappen uit om de App-bron van AEM Forms te verkrijgen:

1. Ga naar pakket shareURL: `https://<server>:<port>/crx/packageshare`.

1. Download het bronpakket. Wanneer u het pakket downloadt, wordt het toegevoegd in het pakketbeheer van AEM Forms.
1. Ga na het downloaden naar: `https://<server>:<port>/crx/packmgr/index.jsp`, en installeer `adobe-aemfd-forms-app-src-pkg-<version>.zip`.

1. Open het archief met de broncode `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in uw browser om dit te downloaden.
Het bronpakket wordt gedownload op uw apparaat.

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip`afbeelding weergegeven.

![mws-content](assets/mws-content.png)

In de volgende tabel vindt u de inhoud van de `adobe-lc-mobileworkspace-src-[version]/ios` map.

<table>
 <tbody>
  <tr>
   <th><p>Map</p> </th>
   <th><p>Inhoud</p> </th>
  </tr>
  <tr>
   <td><p><code>CordovaLib</code></p> </td>
   <td><p>PhoneGap SDK 6.4.0</p> </td>
  </tr>
  <tr>
   <td><p><code>AEM Forms</code></p> </td>
   <td><p>Bronnen, PhoneGap-plug-ins en de hoofdmodule van de toepassing</p> </td>
  </tr>
  <tr>
   <td><p><code>AEM Forms.xcodeproj</code></p> </td>
   <td><p>Xcode-project voor app AEM Forms</p> </td>
  </tr>
  <tr>
   <td><p><code>www</code></p> </td>
   <td><p>HTML-, CSS-, afbeeldings- en JavaScript-bestanden voor het app-project AEM Forms</p> </td>
  </tr>
 </tbody>
</table>

Voor gedetailleerde informatie over het ondertekenen van code en het toevoegen van apparaten aan de iOS Provisioning Portal, zie de Opstelling van de Ondertekening van de Code [iOS, Proces, en het Oplossen van problemen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html).

## Standaard AEM Forms-app ontwikkelen {#set-up-the-xcode-project}

1. Voer de volgende stappen uit om een project in Xcode op te zetten en een het ondertekenen identiteit te verstrekken:

   Meld u aan bij uw Mac-computer waarop Xcode en iOS SDK zijn geïnstalleerd en geconfigureerd.

1. Kopieer het `adobe-lc-mobileworkspace-src-<version>.zip` archief van de map Downloads naar `[User_Home]/Projects/`.
1. Extraheer het archief in de `[User_Home]/Projects/[your-project]`map.
1. Navigeer naar de map ` [User_Home]/Projects/ `[your-project]`/adobe-lc-mobileworkspace-src-[version]/ios` .
1. Open het `AEM Forms.xcodeproj` project in Xcode.
1. Klik op **AEM-formulieren** onder **DOELSTELLINGEN** en selecteer **AEM-formulieren**. Selecteer het tabblad **Build Settings** , zoek de sectie **Code Signing Entitlement** , en voer in de velden Debug and Release een van de volgende handelingen uit:

   * Laat de velden ongespecificeerd om een standaard mobiele werkruimte-app te maken
   * Geef de velden op die moeten worden beschreven in [Een app voor beveiligde AEM-formulieren voor iOS](/help/forms/using/building-secure-mobile-workspace-app.md) maken om een veilige app voor AEM-formulieren te maken.

1. Klik in het tabblad **Build Settings** op **All** (Alles **) en klik vervolgens op** Combinate.
1. Vouw in de lijst **Instellingen** de optie **Code ondertekenen** uit.
1. Selecteer de gewenste handtekening voor Identiteit **ondertekening** van code. Voor gedetailleerde informatie over, het creëren van nieuwe handtekeningen, zie het [Creëren en het Downloaden van de Profielen](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html)van de Levering van de Ontwikkeling.
1. Zorg ervoor dat dezelfde handtekening is geselecteerd voor **Foutopsporing**, **Geen** en **Elke iOS SDK**.
1. Vervang de volgende code in het `AEM Forms-info.plist` bestand:

   ```java
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSAllowsArbitraryLoads</key>
   <true/>
   </dict>
   ```

   met de volgende code te vervangen `yourserver.com` door een geschikte hostnaam voor uw server.

   ```java
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSExceptionDomains</key>
   <dict>
   <key>yourserver.com</key>
   <dict>
   <!-Include to allow subdomains->
   <key>NSIncludesSubdomains</key>
   <true/>
   <!-Include to allow HTTP requests->
   <key>NSTemporaryExceptionAllowsInsecureHTTPLoads</key>
   <true/>
   <!-Include to support forward secrecy->
   <key>NSExceptionRequiresForwardSecrecy</key>
   <false/>
   <!-Include to specify minimum TLS version->
   <key>NSTemporaryExceptionMinimumTLSVersion</key>
   <string>TLSv1.1</string>
   </dict>
   </dict>
   </dict>
   ```

   >[!NOTE]
   >
   >Deze stap is alleen vereist als de app AEM Forms verbinding moet maken met een server die niet voldoet aan de beveiligingsvereisten voor het transport van de app.

1. Selecteer onder **PROJECT** de optie **AEM-formulieren** en zorg ervoor dat de juiste handtekening is geselecteerd voor **Code Signing Identity**, **Debug**, **Release** **** en Any iOS SDK.
1. Sluit een iPad met provisioning aan op een Mac-computer.
1. Selecteer het geleverde apparaat voor het **project van Vormen** AEM.

   ![ipad](assets/ipad.png)

   Er is een apparaat met provisioning, iPad AIR 2, geselecteerd.

1. Selecteer **Product** > **Reinigen**.
1. Selecteer **Product** > **Bouwstijl**.

## Het installatieprogramma voor de app AEM Forms maken {#build-the-installer-for-the-mobile-workspace-app}

U moet het Xcode-project archiveren om het installatieprogramma (een .ipa-bestand) en een eigenschappenlijst (een .plist-bestand) te maken. Het eigenschappenlijstbestand bevat configuratiegegevens van de interne app die wordt gehost, zoals de naam en de hostlocatie van de app. Zie Informatie [over bestanden](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html)in de eigenschappenlijst Informatie voor meer informatie over het eigenschappenlijstbestand.

1. Sluit een iPad met provisioning aan op een Mac-computer. Voor gedetailleerde informatie over het leveren van een iPad raadpleegt u [Ontwikkelingshulpprogramma&#39;s maken en downloaden](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html)
1. Selecteer het geleverde apparaat voor het **project van Vormen** AEM.

   ![ipad-1](assets/ipad-1.png)

   Er is een apparaat met provisioning, iPad AIR 2, geselecteerd.

1. Selecteer **Product** > **Reinigen**.
1. Selecteer **Product** > **Bouwstijl**.
1. Selecteer **Product** > **Archief**.
1. Selecteer in de Organizer - Archieven het meest recente archief van uw project en klik op **Distribueren**.
1. Selecteer **Opslaan voor Enterprise of Ad hoc-implementatie** als de distributiemethode en klik op **Volgende**.
1. Selecteer de gewenste **Code Signing Identity** en klik op **Next**. Klik op **Toestaan** om de handtekening toe te passen.
1. Geef een naam op voor de app en selecteer **Opslaan voor Enterprise Distribution**.
1. Geef de **toepassings-URL** voor de app op. Geef bijvoorbeeld een URL op om de toepassing op een CRX-server te hosten. `https://[LC_host]:'port'/lc/content/distribution/mobileworkspace/APP_NAME.ipa`
1. Geef AEM-formulieren op in het veld **Titel** .
1. Klik op **Opslaan** en sluit Xcode.

   Op de opgegeven locatie worden een installatiebestand `AEM Forms.ipa`en een bestand met een eigenschappenlijst `AEM Forms-info.plist`gemaakt.

1. Open het `AEM Forms-info.plist` bestand in een editor.
1. Vervang alle spaties in de URL van het .ipa-bestand door %20.
1. Sla het `AEM Forms-info.plist` bestand op en sluit het.