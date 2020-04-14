---
title: Een veilige app voor AEM-formulieren voor iOS maken
seo-title: Een veilige app voor AEM-formulieren voor iOS maken
description: Stappen om een veilige app voor AEM Forms te maken.
seo-description: Stappen om een veilige app voor AEM Forms te maken.
uuid: 6c4b160f-4d0c-4976-9609-9196795b6c8e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 90cd8ba5-4f47-4074-bc54-6a7bb8afe256
translation-type: tm+mt
source-git-commit: 49da3dbe590f70b98185a6bc330db6077dc864c0

---


# Een veilige app voor AEM-formulieren voor iOS maken {#building-a-secure-aem-forms-app-for-ios}

U moet het Xcode-project voor de app AEM Forms archiveren om het installatieprogramma (een .ipa-bestand) en een eigenschappenlijst (een .plist-bestand) te maken. Het eigenschappenlijstbestand bevat configuratiegegevens van de interne app die wordt gehost, zoals de naam en de hostlocatie van de app. Zie Informatie [over bestanden](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html)in de eigenschappenlijst Informatie voor meer informatie over het eigenschappenlijstbestand.

1. Meld u aan bij de volgende website:

   [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Maak een toepassings-id. Zie Toepassings-id&#39;s [maken en configureren voor gedetailleerde stappen voor het maken van een toepassings-id](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Klik op Toepassings-id **[!UICONTROL configureren om de bundle-id voor de iOS-toepassing voor uw app te configureren]**.
1. Selecteer onder aan de webpagina de optie **[!UICONTROL Inschakelen voor gegevensbescherming]**. Geef de opties voor gegevensbescherming op.

   Klik op **[!UICONTROL Gereed]**.

1. Navigeer naar Provisioning->Distributie en maak een nieuw profiel met de toepassings-id die in stap 3 is geconfigureerd.
1. Download het inrichtingsprofiel en voeg dit toe aan de Xcode en de iPad.
1. Meld u aan bij de Mac-computer waarop Xcode en iOS SDK zijn geïnstalleerd en geconfigureerd.
1. Open het `AEM Forms.xcodeproj` project in Xcode.
1. Klik op **[!UICONTROL AEM-formulieren]** onder **[!UICONTROL DOELSTELLINGEN]** en selecteer **[!UICONTROL AEM-formulieren]**. Selecteer het tabblad **[!UICONTROL Build Settings]** , zoek de sectie **[!UICONTROL Code Signing Entitlement]** en selecteer in het vervolgkeuzemenu Entitlements de optie **[!UICONTROL LC Enterprise]** .
1. Zoek en open het `LC Enterprise.entitlements` bestand in de Xcode om het te bewerken. Voeg onder de **XCode-machtigingen** hetzelfde sleutelwaardepaar toe als in het inrichtingsprofiel.
1. Klik in het tabblad **[!UICONTROL Build Settings]** op **[!UICONTROL All]** (Alles **[!UICONTROL ) en klik vervolgens op]** Combinate.
1. Vouw in de lijst **[!UICONTROL Instellingen]** de optie **[!UICONTROL Code ondertekenen]** uit.
1. Selecteer de gewenste handtekening voor Identiteit **[!UICONTROL ondertekening]** van code. Zorg ervoor dat dezelfde handtekening is geselecteerd voor **[!UICONTROL Foutopsporing]**, **[!UICONTROL Geen]** en **[!UICONTROL Elke iOS SDK]**.
1. Selecteer onder **[!UICONTROL PROJECT]** de optie **[!UICONTROL AEM-formulieren]** en zorg ervoor dat de juiste handtekening is geselecteerd voor **[!UICONTROL Code Signing Identity]**, **[!UICONTROL Debug]**, **[!UICONTROL Release]** **** en Any iOS SDK.
1. De app AEM Forms maken en distribueren. Zie [Het installatieprogramma voor de app](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app)AEM Forms maken voor gedetailleerde instructies voor het maken en distribueren van de app AEM Forms.
