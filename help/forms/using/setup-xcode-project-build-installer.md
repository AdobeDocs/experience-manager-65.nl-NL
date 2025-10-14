---
title: Het Xcode-project instellen en de iOS-app ontwikkelen
description: Hierin wordt uitgelegd hoe u een standaard AEM Forms-app voor iOS maakt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
docset: aem65
exl-id: 78ce6107-8821-47d6-86ab-7ab968945e7c
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 0%

---

# Het Xcode-project instellen en de iOS-app ontwikkelen{#set-up-the-xcode-project-and-build-the-ios-app}

AEM Forms biedt de volledige broncode van de AEM Forms-app. De bron bevat alle componenten om een aangepaste AEM Forms-app te maken. Het broncodearchief, `adobe-lc-mobileworkspace-src-<version>.zip` , maakt deel uit van het `adobe-aemfd-forms-app-src-pkg-<version>.zip` -pakket voor softwaredistributie.

Voer de volgende stappen uit om de AEM Forms-toepassingsbron op te halen:

1. Open [&#x200B; Distributie van de Software &#x200B;](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [&#x200B; Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=nl-NL) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

1. Als u het broncodearchief wilt downloaden, opent u `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in uw browser.
Het bronpakket wordt gedownload op uw apparaat.

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip` weergegeven.

![&#x200B; mws-content &#x200B;](assets/mws-content.png)

In de volgende tabel wordt de inhoud van de map `adobe-lc-mobileworkspace-src-[version]/ios` beschreven.

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
   <td><p>HTML-, CSS-, afbeeldings- en JavaScript-bestanden voor het AEM Forms-app-project</p> </td>
  </tr>
 </tbody>
</table>

Voor gedetailleerde informatie over het Ondertekenen van de Code en het toevoegen van apparaten aan het Portaal van de Levering van iOS, zie [&#x200B; de Ondertekenende Opstelling van de Code van iOS, Proces, en het Oplossen van problemen &#x200B;](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html).

## Standaard AEM Forms-app ontwikkelen {#set-up-the-xcode-project}

1. Voer de volgende stappen uit om een project in Xcode op te zetten en een het ondertekenen identiteit te verstrekken:

   Meld u aan bij uw Mac-computer waarop Xcode en iOS SDK zijn geïnstalleerd en geconfigureerd.

1. Kopieer het archief van `adobe-lc-mobileworkspace-src-<version>.zip` van de map Downloads naar `[User_Home]/Projects/` .
1. Extraheer het archief in de `[User_Home]/Projects/[your-project]` folder.
1. Navigeer aan de ` [User_Home]/Projects/ `[ uw-project ]`/adobe-lc-mobileworkspace-src-[version]/ios` folder.
1. Open het `AEM Forms.xcodeproj` -project in Xcode.
1. Klik **AEM Forms**, onder **DOELEN**, uitgezochte **AEM Forms**. Selecteer het **Bouw Montages** lusje, bepaal de plaats van de **Code die de sectie van de Entitlement** ondertekenen, en in zuivert en maakt gebieden van de Versie één van het volgende:

   * Laat de velden ongespecificeerd om een standaard Mobile Workspace-app te maken
   * Specificeer de gebieden aan zoals verklaard in [&#x200B; Bouwend een Veilige app van AEM Forms voor iOS &#x200B;](/help/forms/using/building-secure-mobile-workspace-app.md) om een veilige app van AEM Forms te bouwen.

1. In het **bouwt Montages** lusje, klik **allen** en klik dan **Gecombineerd**.
1. Van de **lijst van Montages**, breid **Code die** ondertekenen uit.
1. Voor **Code het Ondertekenen Identiteit**, selecteer de aangewezen handtekening. Voor gedetailleerde informatie over, creërend nieuwe handtekeningen, zie [&#x200B; Creërend en Downloadend de Profielen van de Levering van de Ontwikkeling &#x200B;](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html).
1. Zorg ervoor dat de zelfde handtekening voor **wordt geselecteerd zuivert**, **Versie**, en **om het even welke iOS SDK**.
1. Vervang de volgende code in het `AEM Forms-info.plist` -bestand:

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

1. Onder **PROJECT**, selecteer **AEM Forms** en zorg ervoor dat de aangewezen handtekening voor **Code die Identiteit ondertekenen** wordt geselecteerd, **zuivert**, **Versie** en **Om het even welke SDK van iOS**.
1. Sluit een iPad met provisioning aan op een Mac-computer.
1. Selecteer het provisioned apparaat voor het **AEM Forms** project.

   ![&#x200B; ipad &#x200B;](assets/ipad.png)

   Er is een apparaat met provisioning, iPad Air 2, geselecteerd.

1. Selecteer **Product** > **Schoon**.
1. Selecteer **Product** > **bouwt**.

## Het installatieprogramma voor de AEM Forms-app maken {#build-the-installer-for-the-mobile-workspace-app}

U moet het Xcode-project archiveren om het installatieprogramma (een .ipa-bestand) en een eigenschappenlijst (een .plist-bestand) te maken. Het eigenschappenlijstbestand bevat configuratiegegevens van de interne app die wordt gehost, zoals de naam en de hostlocatie van de app. Voor meer informatie over het dossier van de bezitslijst, zie [&#x200B; Ongeveer de Dossiers van de Lijst van het Bezit van de Informatie &#x200B;](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Sluit een iPad met provisioning aan op een Mac-computer. Voor gedetailleerde informatie over levering een iPad, zie [&#x200B; Creërend en het Downloaden van de Profielen van de Levering van de Ontwikkeling &#x200B;](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/CreatingYourTeamProvisioningProfile/CreatingYourTeamProvisioningProfile.html)
1. Selecteer het provisioned apparaat voor het **AEM Forms** project.

   ![&#x200B; iPad-1 &#x200B;](assets/ipad-1.png)

   Er is een apparaat met provisioning, iPad Air 2, geselecteerd.

1. Selecteer **Product** > **Schoon**.
1. Selecteer **Product** > **bouwt**.
1. Selecteer **Product** > **Archief**.
1. In Organisator - Archieven, selecteer het recentste archief van uw project en klik **verdelen**.
1. Selecteer **sparen voor Onderneming of Ad hoc Plaatsing** als methode van distributie en klik **daarna**.
1. Selecteer de aangewezen **Code die Identiteit** ondertekenen en klik **daarna**. Klik **toestaan** om de handtekening toe te passen.
1. Verstrek naam van app en selecteer **sparen voor de Distributie van de Onderneming**.
1. Verstrek **Toepassing URL** voor app. Geef bijvoorbeeld URL `https://[LC_host]:'port'/lc/content/distribution/mobileworkspace/APP_NAME.ipa` op als u de toepassing op een CRX-server wilt hosten.
1. Op het **gebied van de Titel**, specificeer AEM Forms.
1. Klik **sparen** en sluit Xcode.

   Op de opgegeven locatie wordt een installatiebestand ( `AEM Forms.ipa` ) en een bestand met de eigenschappenlijst ( `AEM Forms-info.plist` ) gemaakt.

1. Open het `AEM Forms-info.plist` -bestand in een editor.
1. Vervang alle spaties in de URL van het .ipa-bestand door %20.
1. Sla het `AEM Forms-info.plist` -bestand op en sluit het.
