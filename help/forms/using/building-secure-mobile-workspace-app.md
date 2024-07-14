---
title: Een veilige AEM Forms-app voor iOS maken
description: Leer hoe u een veilige AEM Forms-app voor iOS maakt door het Xcode-project te archiveren. Hiermee maakt u een installatiebestand (een .ipa-bestand) en een eigenschappenlijstbestand (een .plist-bestand).
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 12cc2027-ae94-40c3-a7d1-553469426114
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Een veilige AEM Forms-app voor iOS maken {#building-a-secure-aem-forms-app-for-ios}

U moet het Xcode-project voor de AEM Forms-app archiveren om het installatieprogramma (een .ipa-bestand) en een eigenschappenlijst (een .plist-bestand) te maken. Het eigenschappenlijstbestand bevat configuratiegegevens van de interne app die wordt gehost, zoals de naam en de hostlocatie van de app. Voor meer informatie over het dossier van de bezitslijst, zie [ Ongeveer de Dossiers van de Lijst van het Bezit van de Informatie ](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Meld u aan bij de volgende website:

   [ https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Maak een toepassings-id. Voor gedetailleerde stappen om een identiteitskaart van de Toepassing tot stand te brengen, zie [ Creërend en Vormend App IDs ](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Klik op **[!UICONTROL Configure App ID]** om de bundle-id voor de iOS-toepassing voor uw app te configureren.
1. Selecteer onder aan de webpagina de optie **[!UICONTROL Enable for Data Protection]** . Geef de opties voor gegevensbescherming op.

   Klik op **[!UICONTROL Done]**.

1. Navigeer naar Provisioning>Distributie en maak een nieuw profiel met de toepassings-id die in stap 3 is geconfigureerd.
1. Download en voeg het inrichtingsprofiel toe aan de Xcode en de iPad.
1. Meld u aan bij uw Mac-computer waarop Xcode en iOS SDK zijn geïnstalleerd en geconfigureerd.
1. Open het `AEM Forms.xcodeproj` -project in Xcode.
1. Klik op **[!UICONTROL AEM Forms]** onder **[!UICONTROL TARGETS]** en selecteer **[!UICONTROL AEM Forms]** . Selecteer de tab **[!UICONTROL Build Settings]** , zoek de sectie **[!UICONTROL Code Signing Entitlement]** en selecteer in het vervolgkeuzemenu Entitlements de optie **[!UICONTROL LC Enterprise]** .
1. Zoek en open het `LC Enterprise.entitlements` -bestand in de Xcode om het te bewerken. Onder de **XCode toestemmingen**, voeg het zelfde zeer belangrijk-waardepaar zoals huidig in uw inrichtingsprofiel toe.
1. Klik op het tabblad **[!UICONTROL Build Settings]** op **[!UICONTROL All]** en klik vervolgens op **[!UICONTROL Combined]** .
1. Vouw in de lijst **[!UICONTROL Settings]** **[!UICONTROL Code Signing]** uit.
1. Selecteer bij **[!UICONTROL Code Signing Identity]** de juiste handtekening. Zorg ervoor dat dezelfde handtekening is geselecteerd voor **[!UICONTROL Debug]** , **[!UICONTROL Release]** en **[!UICONTROL Any iOS SDK]** .
1. Selecteer onder **[!UICONTROL PROJECT]** de optie **[!UICONTROL AEM Forms]** en controleer of de juiste handtekening is geselecteerd voor **[!UICONTROL Code Signing Identity]** , **[!UICONTROL Debug]** , **[!UICONTROL Release]** en **[!UICONTROL Any iOS SDK]** .
1. AEM Forms-app ontwikkelen en distribueren. Voor gedetailleerde instructies om AEM Forms app te bouwen en te verspreiden, zie [ de installateur voor AEM Forms app ](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app) bouwen.
