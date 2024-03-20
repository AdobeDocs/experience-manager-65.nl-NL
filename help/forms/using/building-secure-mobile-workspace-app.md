---
title: Een veilige AEM Forms-app voor iOS maken
description: Leer hoe u een veilige AEM Forms-app voor iOS maakt door het Xcode-project te archiveren. Hiermee maakt u een installatiebestand (een .ipa-bestand) en een eigenschappenlijstbestand (een .plist-bestand).
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: 12cc2027-ae94-40c3-a7d1-553469426114
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Een veilige AEM Forms-app voor iOS maken {#building-a-secure-aem-forms-app-for-ios}

U moet het Xcode-project voor de AEM Forms-app archiveren om het installatieprogramma (een .ipa-bestand) en een eigenschappenlijst (een .plist-bestand) te maken. Het eigenschappenlijstbestand bevat configuratiegegevens van de interne app die wordt gehost, zoals de naam en de hostlocatie van de app. Voor meer informatie over het dossier van de bezitslijst, zie [Informatie over eigenschappenbestanden](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Meld u aan bij de volgende website:

   [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Maak een toepassings-id. Ga voor gedetailleerde stappen om een toepassings-id te maken naar [Toepassings-id&#39;s maken en configureren](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Als u de bundle-id voor de iOS-toepassing voor uw app wilt configureren, klikt u op **[!UICONTROL Configure App ID]**.
1. Selecteer onder aan de webpagina de optie **[!UICONTROL Enable for Data Protection]**. Geef de opties voor gegevensbescherming op.

   Klik op **[!UICONTROL Done]**.

1. Navigeer naar Provisioning>Distributie en maak een nieuw profiel met de toepassings-id die in stap 3 is geconfigureerd.
1. Download en voeg het inrichtingsprofiel toe aan de Xcode en de iPad.
1. Meld u aan bij uw Mac-computer waarop Xcode en iOS SDK zijn geïnstalleerd en geconfigureerd.
1. Open de `AEM Forms.xcodeproj` project in Xcode.
1. Klikken **[!UICONTROL AEM Forms]**, onder **[!UICONTROL TARGETS]**, selecteert u **[!UICONTROL AEM Forms]**. Selecteer de **[!UICONTROL Build Settings]** tabblad, zoekt u de **[!UICONTROL Code Signing Entitlement]** en selecteert u in het vervolgkeuzemenu Entitlements de optie **[!UICONTROL LC Enterprise]** -optie.
1. Zoek en open de `LC Enterprise.entitlements` in de Xcode voor bewerking. Onder de **XCode-rechten** voegt u hetzelfde sleutelwaardepaar toe als in uw inrichtingsprofiel.
1. In de **[!UICONTROL Build Settings]** tabblad, klikt u op **[!UICONTROL All]** en klik vervolgens op **[!UICONTROL Combined]**.
1. Van de **[!UICONTROL Settings]** lijst, uitbreiden **[!UICONTROL Code Signing]**.
1. Voor **[!UICONTROL Code Signing Identity]** selecteert u de gewenste handtekening. Zorg ervoor dat dezelfde handtekening is geselecteerd voor **[!UICONTROL Debug]**, **[!UICONTROL Release]**, en **[!UICONTROL Any iOS SDK]**.
1. Onder **[!UICONTROL PROJECT]**, selecteert u **[!UICONTROL AEM Forms]** en zorgt ervoor dat de juiste handtekening wordt geselecteerd **[!UICONTROL Code Signing Identity]**, **[!UICONTROL Debug]**, **[!UICONTROL Release]** en **[!UICONTROL Any iOS SDK]**.
1. AEM Forms-app ontwikkelen en distribueren. Ga voor gedetailleerde instructies voor het samenstellen en distribueren van de AEM Forms-app naar [Het installatieprogramma voor de AEM Forms-app maken](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app).
