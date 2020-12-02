---
title: Een veilige AEM Forms-app voor iOS maken
seo-title: Een veilige AEM Forms-app voor iOS maken
description: Stappen om een veilige AEM Forms-app te maken.
seo-description: Stappen om een veilige AEM Forms-app te maken.
uuid: 6c4b160f-4d0c-4976-9609-9196795b6c8e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
discoiquuid: 90cd8ba5-4f47-4074-bc54-6a7bb8afe256
translation-type: tm+mt
source-git-commit: 49da3dbe590f70b98185a6bc330db6077dc864c0
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# Een veilige AEM Forms-app voor iOS maken {#building-a-secure-aem-forms-app-for-ios}

U moet het Xcode-project voor de AEM Forms-app archiveren om het installatieprogramma (een .ipa-bestand) en een eigenschappenlijst (een .plist-bestand) te maken. Het eigenschappenlijstbestand bevat configuratiegegevens van de interne app die wordt gehost, zoals de naam en de hostlocatie van de app. Voor meer informatie over het dossier van de bezitslijst, zie [Ongeveer de Dossiers van de Lijst van het Bezit van de Informatie](https://developer.apple.com/library/ios/#documentation/general/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html).

1. Meld u aan bij de volgende website:

   [https://developer.apple.com/account/ios/identifier/bundle](https://developer.apple.com/account/ios/identifier/bundle)

1. Maak een toepassings-id. Voor gedetailleerde stappen om een identiteitskaart van de Toepassing tot stand te brengen, zie [Creërend en Vormend App IDs](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html).
1. Als u de bundle-id voor de iOS-toepassing voor uw app wilt configureren, klikt u op **[!UICONTROL Configure App ID]**.
1. Selecteer **[!UICONTROL Enable for Data Protection]** onder aan de webpagina. Geef de opties voor gegevensbescherming op.

   Klik op **[!UICONTROL Done]**.

1. Navigeer naar Provisioning->Distributie en maak een nieuw profiel met de toepassings-id die in stap 3 is geconfigureerd.
1. Download het inrichtingsprofiel en voeg dit toe aan de Xcode en de iPad.
1. Meld u aan bij de Mac-computer waarop Xcode en iOS SDK zijn geïnstalleerd en geconfigureerd.
1. Open het `AEM Forms.xcodeproj` project in Xcode.
1. Klik **[!UICONTROL AEM Forms]**, onder **[!UICONTROL TARGETS]**, selecteer **[!UICONTROL AEM Forms]**. Selecteer het tabblad **[!UICONTROL Build Settings]**, zoek de sectie **[!UICONTROL Code Signing Entitlement]** en selecteer in het vervolgkeuzemenu Entitlements de optie **[!UICONTROL LC Enterprise]**.
1. Zoek en open het `LC Enterprise.entitlements`-bestand in de Xcode om het te bewerken. Voeg onder **XCode toeslagrechten** hetzelfde sleutelwaardepaar toe als in uw inrichtingsprofiel.
1. Klik op het tabblad **[!UICONTROL Build Settings]** op **[!UICONTROL All]** en klik vervolgens op **[!UICONTROL Combined]**.
1. Vouw **[!UICONTROL Code Signing]** in de lijst **[!UICONTROL Settings]** uit.
1. Selecteer voor **[!UICONTROL Code Signing Identity]** de juiste handtekening. Zorg ervoor dat dezelfde handtekening is geselecteerd voor **[!UICONTROL Debug]**, **[!UICONTROL Release]** en **[!UICONTROL Any iOS SDK]**.
1. Selecteer **[!UICONTROL PROJECT]** onder **[!UICONTROL AEM Forms]** en zorg ervoor dat de juiste handtekening is geselecteerd voor **[!UICONTROL Code Signing Identity]**, **[!UICONTROL Debug]**, **[!UICONTROL Release]** en **[!UICONTROL Any iOS SDK]**.
1. AEM Forms-app ontwikkelen en distribueren. Zie [Het installatieprogramma voor de AEM Forms-app maken](setup-xcode-project-build-installer.md#build-the-installer-for-the-mobile-workspace-app) voor gedetailleerde instructies voor het maken en distribueren van de AEM Forms-app.
