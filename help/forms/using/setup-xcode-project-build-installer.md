---
title: Het Xcode-project instellen en de iOS-app ontwikkelen
description: Hierin wordt uitgelegd hoe u een standaard AEM Forms-app voor iOS maakt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 78ce6107-8821-47d6-86ab-7ab968945e7c
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 0%

---

# Het Xcode-project instellen en de iOS-app ontwikkelen{#set-up-the-xcode-project-and-build-the-ios-app}

AEM Forms biedt de volledige broncode van de AEM Forms-app. De bron bevat alle componenten om een aangepaste AEM Forms-app te maken. Het broncodearchief, `adobe-lc-mobileworkspace-src-<version>.zip` maakt deel uit van de `adobe-aemfd-forms-app-src-pkg-<version>.zip` pakket over Softwaredistributie.

Voer de volgende stappen uit om de AEM Forms-toepassingsbron op te halen:

1. Openen [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteren **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de **[!UICONTROL Filters]** sectie:
   1. Selecteren **[!UICONTROL Forms]** van de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt ook de opdracht **[!UICONTROL Search Downloads]** om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem. Selecteer **[!UICONTROL Accept EULA Terms]** en selecteert u **[!UICONTROL Download]**.
1. Openen [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)  en klik op **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

1. Als u het broncodearchief wilt downloaden, opent u `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in uw browser.
Het bronpakket wordt gedownload op uw apparaat.

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip`.

![mws-content](assets/mws-content.png)

De volgende tabel bevat de inhoud van de `adobe-lc-mobileworkspace-src-[version]/ios` map.

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

Voor gedetailleerde informatie over het ondertekenen van code en het toevoegen van apparaten aan het Portaal van de Levering van iOS, zie [iOS Code Signing Setup, Process en Troubleshooting](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html).

## Standaard AEM Forms-app ontwikkelen {#set-up-the-xcode-project}

1. Voer de volgende stappen uit om een project in Xcode op te zetten en een het ondertekenen identiteit te verstrekken:

   Meld u aan bij uw Mac-computer waarop Xcode en iOS SDK zijn geïnstalleerd en geconfigureerd.

1. De `adobe-lc-mobileworkspace-src-<version>.zip` archiveren van de map Downloads naar `[User_Home]/Projects/`.
1. Het archief in het dialoogvenster `[User_Home]/Projects/[your-project]`directory.
1. Ga naar de ` [User_Home]/Projects/ `[uw project]`/adobe-lc-mobileworkspace-src-[version]/ios` directory.
1. Open de `AEM Forms.xcodeproj` project in Xcode.
1. Klikken **AEM Forms**, onder **DOELSTELLINGEN**, selecteert u **AEM Forms**. Selecteer de **Build-instellingen** tabblad, zoekt u de **Code Signing Entitlement** en voert u in de velden Foutopsporing en Geen een van de volgende handelingen uit:

   * Laat de velden ongespecificeerd om een standaard mobiele werkruimte-app te maken
   * Geef de velden op die u wilt opgeven zoals wordt uitgelegd in [Een Secure AEM Forms-app voor iOS maken](/help/forms/using/building-secure-mobile-workspace-app.md) om een veilige AEM Forms-app te maken.

1. In de **Build-instellingen** tabblad, klikt u op **Alles** en klik vervolgens op **Gecombineerd**.
1. Van de **Instellingen** lijst, uitbreiden **Code-ondertekening**.
1. Voor **Identiteit ondertekening code** selecteert u de gewenste handtekening. Voor meer informatie over het maken van nieuwe handtekeningen raadpleegt u [Ontwikkelinrichtingsprofielen maken en downloaden](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html).
1. Zorg ervoor dat dezelfde handtekening is geselecteerd voor **Foutopsporing**, **Geen**, en **Willekeurige iOS SDK**.
1. Vervang de volgende code in de `AEM Forms-info.plist` bestand:

   ```xml
   <key>NSAppTransportSecurity</key>
   <dict>
   <key>NSAllowsArbitraryLoads</key>
   <true/>
   </dict>
   ```

   met het volgende tijdens het vervangen `yourserver.com` met een geschikte hostnaam voor uw server.

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

1. Onder **PROJECT**, selecteert u **AEM Forms** en zorgt ervoor dat de juiste handtekening wordt geselecteerd **Identiteit ondertekening code**, **Foutopsporing**, **Geen** en **Willekeurige iOS SDK**.
1. Sluit een iPad met provisioning aan op een Mac-computer.
1. Selecteer het apparaat waarvoor de provisioning is uitgevoerd **AEM Forms** project.

   ![ipad](assets/ipad.png)

   Er is een apparaat met provisioning, iPad Air 2, geselecteerd.

1. Selecteren **Product** > **Reinigen**.
1. Selecteren **Product** > **Opbouwen**.

## Het installatieprogramma voor de AEM Forms-app maken {#build-the-installer-for-the-mobile-workspace-app}

U moet het Xcode-project archiveren om het installatieprogramma (een .ipa-bestand) en een eigenschappenlijst (een .plist-bestand) te maken. Het eigenschappenlijstbestand bevat configuratiegegevens van de interne app die wordt gehost, zoals de naam en de hostlocatie van de app. Voor meer informatie over het dossier van de bezitslijst, zie [Informatie over eigenschappenbestanden](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Sluit een iPad met provisioning aan op een Mac-computer. Ga voor meer informatie over provisioning van een iPad naar [Ontwikkelinrichtingsprofielen maken en downloaden](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html)
1. Selecteer het apparaat waarvoor de provisioning is uitgevoerd **AEM Forms** project.

   ![ipad-1](assets/ipad-1.png)

   Er is een apparaat met provisioning, iPad Air 2, geselecteerd.

1. Selecteren **Product** > **Reinigen**.
1. Selecteren **Product** > **Opbouwen**.
1. Selecteren **Product** > **Archief**.
1. Selecteer in de Organizer - Archieven het meest recente archief van uw project en klik op **Distribueren**.
1. Selecteren **Opslaan voor Enterprise- of ad-hocimplementatie** als de verspreidingsmethode en klik op **Volgende**.
1. Selecteer de juiste **Identiteit ondertekening code** en klik op **Volgende**. Klikken **Toestaan** om de handtekening toe te passen.
1. Geef een naam op voor de app en selecteer **Opslaan voor Enterprise Distribution**.
1. Geef de **Toepassings-URL** voor de app. Geef bijvoorbeeld een URL op om de toepassing op een CRX-server te hosten `https://[LC_host]:'port'/lc/content/distribution/mobileworkspace/APP_NAME.ipa`.
1. In de **Titel** -veld, geeft u AEM Forms op.
1. Klikken **Opslaan** en sluit Xcode.

   een installatiebestand, `AEM Forms.ipa`en het eigenschappenlijstbestand, `AEM Forms-info.plist`, worden op de opgegeven locatie gemaakt.

1. Open de `AEM Forms-info.plist` in een editor.
1. Vervang alle spaties in de URL van het .ipa-bestand door %20.
1. Opslaan en het dialoogvenster sluiten `AEM Forms-info.plist` bestand.
