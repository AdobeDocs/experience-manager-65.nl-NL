---
title: Mobiele toepassingen ontwikkelen in AEM
description: Volg deze pagina om te beginnen met het ontwikkelen van mobiele toepassingen in AEM met Adobe PhoneGap Enterprise.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: cf8ba05c-6dcd-4880-b8bf-72382118cd80
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Mobiele toepassingen ontwikkelen in AEM {#developing-mobile-applications-in-aem}

{{ue-over-mobile}}

AEM maakt gebruik van Adobe PhoneGap en Adobe Publishing Solutions, waarmee u zowel content-rich als op toepassingen gebaseerde mobiele toepassingen voor meerdere platforms kunt maken en beheren:

* Beheer al uw bedrijven mobiele apps op één locatie.
* Bekijk toepassingen in ontwikkelings- en testomgevingen zonder de complexiteit van inrichtingsprofielen en de extra inspanning om uw app te maken en te uploaden voor delen.
* Gebruik de AEM ontwerpomgeving om rijke inhoud voor uw apps te maken en te beheren.
* Gebruik de HTML5 met Adobe PhoneGap om rijke ervaringen met apparaat-inheemse mogelijkheden tot stand te brengen.
* Introduceer HTML5 Webviews aan nieuwe of reeds bestaande **inheemse** toepassingen door Cordova WebViews.
* Maak, curseer en deel rijke multimedia-inhoud via alle leveringskanalen, waaronder web, mobiel-web, mobiele-app en drukwerk.

AEM integreert met de dienst van Adobe PhoneGap Build (`https://build.phonegap.com/`) om de toepassing te vereenvoudigen bouwt en opstelt proces.

**Adobe ContentSync** laat gebruikers toe om pagina en inhoudsupdates over-the-Air (OTA) aan hun apparaten gemakkelijk te downloaden zonder het moeten de toepassing opnieuw installeren of van appStore, Google Play, of andere toepassingsbronnen downloaden.

**Adobe Analytics** is volledig geïntegreerd in AEM apps en staat gedetailleerde het volgen van distributie, geolocatie, werkende systemen, apparaten, klik-stromen, iBeacon het volgen en meer toe.

## Apps maken {#creating-apps}

De ontwikkelaars kunnen de [ AEM Uitrusting van de Aanzet PhoneGap ](https://github.com/Adobe-Marketing-Cloud/aem-phonegap-starter-kit) samen met extra middelen gebruiken die in [ https://github.com/adobe-marketing-cloud-apps ](https://github.com/adobe-marketing-cloud-apps) worden gevonden om AEM toepassingen met PhoneGap, met inbegrip van een verwijzing inheemse app die Cordova Webviews in werking stelt.

De readme voor de Starter Kit Git-opslagplaats bevat een zelfstudie voor het gebruik van de startkit:

* De branding aanpassen
* Gemaakte doelstellingen van de steekproefbouw en plaatsing
* Configuratie van Source-beheeropslagplaats
* Installeren en implementeren in lokale of externe AEM
* Verwijderen uit AEM

>[!NOTE]
>
>De extra bron van de verwijzingsimplementatie, met inbegrip van laboratoria, kan op GitHub [ hier ](https://github.com/adobe-marketing-cloud-apps) en, de &quot;keuken-goot&quot;bron [ hier ](https://github.com/blefebvre/aem-phonegap-kitchen-sink) worden gevonden.

## Ontwikkelen voor IOS 9 en HTTP-hosts {#developing-for-ios-and-http-hosts}

IOS-ontwikkelaars moeten op de hoogte zijn van een open probleem met Cordova-apps die op iOS 9 worden uitgevoerd. Deze kwestie verhindert verzoeken aan onveilige gastheren (zoals *http://localhost:4502*) worden gemaakt. Dit probleem zal worden opgelost met de komende vrijgave van cordova-ios (verbruikt door de CLI van Cordova), maar ondertussen zijn er twee oplossingen beschikbaar:

1. U kunt nu alle iOS 8-simulators zonder problemen gebruiken.
1. Als u iOS 9 moet gebruiken, kunt u de toepassingen -Info.plist (gevonden na uitvoering `cordova platform add ios` in het bestand &quot;&lt;app root>/platformen/ios/&lt;app name>/&lt;app name>-Info.plist&quot;) handmatig bewerken en de volgende eigenschap opnemen:

```
<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key> <true/>

</dict>
```

>[!NOTE]
>
>Voor meer detail op &quot;de Veiligheid van het Vervoer van de Toepassing&quot;, zie de volgende sectie van [ Apple iOS9- prerelease docs ](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW14) en dit [ Stack Overflow bespreking ](https://stackoverflow.com/questions/30751053/ios9-ats-what-about-html5-based-apps/).

## Mobiele toepassingen ontwikkelen in AEM {#developing-mobile-applications-in-aem-1}

* [AEM PhoneGap starten](/help/mobile/starting-aem-phonegap-app.md)
* [Mobiele toepassingen maken](/help/mobile/building-app-mobile-phonegap.md)
* [Een app structureren](/help/mobile/phonegap-structure-an-app.md)
* [Apps maken en bewerken met de toepassingsconsole](/help/mobile/phonegap-apps-console.md)
* [Toepassingen voor één pagina](/help/mobile/phonegap-single-page-applications.md)
* [Apps ontwikkelen met PhoneGap CLI](/help/mobile/phonegap-apps-pg-cli.md)
* [Apparaatfuncties openen](/help/mobile/phonegap-access-device-features.md)
* [App-prestaties bijhouden met Adobe Mobile Analytics](/help/mobile/phonegap-intro-to-app-analytics.md)
* [Adobe Analytics toevoegen aan uw mobiele toepassing](/help/mobile/phonegap-add-analytics-to-apps.md)
* [Pushmeldingen](/help/mobile/phonegap-push-notifications.md)
* [Aanpassing van AEM Mobile-content](/help/mobile/phonegap-aem-mobile-content-personalization.md)
* [De anatomie van een app](/help/mobile/phonegap-apps-arch.md)
* [Is uw hybride app gereed voor AEM Mobile?](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwerpen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)
