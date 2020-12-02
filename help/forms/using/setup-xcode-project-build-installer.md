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
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---


# Stel het Xcode-project in en maak de iOS-app{#set-up-the-xcode-project-and-build-the-ios-app}

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

1. Als u het archief van de broncode wilt downloaden, opent u `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in uw browser.
Het bronpakket wordt gedownload op uw apparaat.

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip` weergegeven.

![mws-content](assets/mws-content.png)

De volgende lijst detailleert inhoud van `adobe-lc-mobileworkspace-src-[version]/ios` omslag.

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
   <td><p>Xcode-project voor AEM Forms-toepassing</p> </td>
  </tr>
  <tr>
   <td><p><code>www</code></p> </td>
   <td><p>HTML-, CSS-, afbeeldings- en JavaScript-bestanden voor het AEM Forms-toepassingsproject</p> </td>
  </tr>
 </tbody>
</table>

Zie [iOS Code Signing Setup, Process en Troubleshooting](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) voor gedetailleerde informatie over het ondertekenen van code en het toevoegen van apparaten aan de iOS Provisioning Portal.

## Standaard AEM Forms-app {#set-up-the-xcode-project} maken

1. Voer de volgende stappen uit om een project in Xcode op te zetten en een het ondertekenen identiteit te verstrekken:

   Meld u aan bij uw Mac-computer waarop Xcode en iOS SDK zijn geïnstalleerd en geconfigureerd.

1. Kopieer het `adobe-lc-mobileworkspace-src-<version>.zip`-archief van de map Downloads naar `[User_Home]/Projects/`.
1. Extraheer het archief in de map `[User_Home]/Projects/[your-project]`.
1. Navigeer aan ` [User_Home]/Projects/ `[uw-project]`/adobe-lc-mobileworkspace-src-[version]/ios` folder.
1. Open het `AEM Forms.xcodeproj` project in Xcode.
1. Klik **AEM Forms**, onder **TARGETS**, selecteer **AEM Forms**. Selecteer het tabblad **Build Settings**, zoek de sectie **Code Signing Entitlement** en voer een van de volgende handelingen uit in de velden Foutopsporing en Geen:

   * Laat de velden ongespecificeerd om een standaard mobiele werkruimte-app te maken
   * Geef de velden op die moeten worden beschreven in [Een Secure AEM Forms-app voor iOS maken](/help/forms/using/building-secure-mobile-workspace-app.md) om een veilige AEM Forms-app te maken.

1. Klik in het tabblad **Instellingen voor samenstellen** op **Alles** en klik vervolgens op **Combineren**.
1. Vouw in de lijst **Instellingen** **Code-ondertekening** uit.
1. Selecteer de gewenste handtekening voor **Identiteit ondertekening code**. Voor gedetailleerde informatie over, het creëren van nieuwe handtekeningen, zie [het Creëren en het Downloaden van de Profielen van de Levering van de Ontwikkeling](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html).
1. Zorg ervoor dat dezelfde handtekening is geselecteerd voor **Foutopsporing**, **Geen** en **Elke iOS SDK**.
1. Vervang de volgende code in het `AEM Forms-info.plist` dossier:

   ```xml
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSAllowsArbitraryLoads</key>
   <true/>
   </dict>
   ```

   met het volgende te vervangen en `yourserver.com` te vervangen door een geschikte hostnaam voor uw server.

   ```xml
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
   >Deze stap is alleen vereist als de AEM Forms-toepassing verbinding moet maken met een server die niet voldoet aan de beveiligingsvereisten voor het vervoer van de app.

1. Selecteer **AEM Forms** onder **PROJECT** en zorg dat de juiste handtekening is geselecteerd voor **Code Signing Identity**, **Debug**, **Release** en **Any iOS SDK**.
1. Sluit een iPad met provisioning aan op een Mac-computer.
1. Selecteer het provisioned apparaat voor het **AEM Forms** project.

   ![ipad](assets/ipad.png)

   Er is een apparaat met provisioning, iPad AIR 2, geselecteerd.

1. Selecteer **Product** > **Clean**.
1. Selecteer **Product** > **Build**.

## Het installatieprogramma voor de AEM Forms-app {#build-the-installer-for-the-mobile-workspace-app} maken

U moet het Xcode-project archiveren om het installatieprogramma (een .ipa-bestand) en een eigenschappenlijst (een .plist-bestand) te maken. Het eigenschappenlijstbestand bevat configuratiegegevens van de interne app die wordt gehost, zoals de naam en de hostlocatie van de app. Voor meer informatie over het dossier van de bezitslijst, zie [Ongeveer de Dossiers van de Lijst van het Bezit van de Informatie](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Sluit een iPad met provisioning aan op een Mac-computer. Zie [Development Provisioning Profiles](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html) maken en downloaden voor gedetailleerde informatie over het leveren van een iPad.
1. Selecteer het provisioned apparaat voor het **AEM Forms** project.

   ![ipad-1](assets/ipad-1.png)

   Er is een apparaat met provisioning, iPad AIR 2, geselecteerd.

1. Selecteer **Product** > **Clean**.
1. Selecteer **Product** > **Build**.
1. Selecteer **Product** > **Archief**.
1. Selecteer in Organizer - Archieven het meest recente archief van uw project en klik op **Distribueren**.
1. Selecteer **Opslaan voor Enterprise- of ad-hocimplementatie** als de verspreidingsmethode en klik op **Volgende**.
1. Selecteer de juiste **Code Signing Identity** en klik **Next**. Klik **Toestaan** om de handtekening toe te passen.
1. Geef een naam op voor de app en selecteer **Opslaan voor Enterprise Distribution**.
1. Geef **Application URL** op voor de app. Als u bijvoorbeeld de toepassing op een CRX-server wilt hosten, voert u URL `https://[LC_host]:'port'/lc/content/distribution/mobileworkspace/APP_NAME.ipa` in.
1. Geef AEM Forms op in het veld **Title**.
1. Klik **Opslaan** en sluit Xcode.

   Een installatiebestand, `AEM Forms.ipa`, en een bestand met de eigenschappenlijst, `AEM Forms-info.plist`, worden gemaakt op de opgegeven locatie.

1. Open het `AEM Forms-info.plist` dossier in een redacteur.
1. Vervang alle spaties in de URL van het .ipa-bestand door %20.
1. Sla het `AEM Forms-info.plist`-bestand op en sluit het.