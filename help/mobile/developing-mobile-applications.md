---
title: Mobiele toepassingen ontwikkelen in AEM
seo-title: Mobiele toepassingen ontwikkelen in AEM
description: Volg deze pagina om te beginnen met het ontwikkelen van mobiele toepassingen in AEM met Adobe PhoneGap Enterprise.
seo-description: Volg deze pagina om te beginnen met het ontwikkelen van mobiele toepassingen in AEM met Adobe PhoneGap Enterprise.
uuid: d8442447-ee04-4bb2-a0d7-17dcc8979dba
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: fd7bcf17-af7e-4bd6-8137-48401d9743c5
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# Mobiele toepassingen ontwikkelen in AEM {#developing-mobile-applications-in-aem}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

AEM maakt gebruik van Adobe PhoneGap en Adobe Publishing Solutions, waarmee u zowel content-rich als op toepassingen gebaseerde mobiele toepassingen voor meerdere platforms kunt maken en beheren:

* Beheer al uw bedrijven mobiele apps op één locatie.
* Bekijk toepassingen in ontwikkelings- en testomgevingen zonder de complexiteit van inrichtingsprofielen en de extra inspanning om uw app te maken en te uploaden voor delen.
* Gebruik de AEM ontwerpomgeving om rijke inhoud voor uw apps te maken en te beheren.
* Gebruik HTML5 met Adobe PhoneGap om rijke ervaringen met apparaat-inheemse mogelijkheden tot stand te brengen.
* Introduceer HTML5 Webviews aan nieuwe of reeds bestaande **inheemse** toepassingen door Cordova WebViews.
* Maak, curseer en deel rijke multimedia-inhoud via alle leveringskanalen, waaronder web, mobiel-web, mobiele-app en drukwerk.

AEM integreert met de Adobe **[PhoneGap Build-service](https://build.phonegap.com/)** om het proces voor het maken en implementeren van toepassingen te vereenvoudigen.

**Met Adobe** ContentSyncets kunnen gebruikers eenvoudig pagina- en inhoudsupdates over-the-Air (OTA) downloaden naar hun apparaten zonder dat ze de toepassing opnieuw hoeven te installeren of moeten downloaden van de appStore, Google Play of andere toepassingsbronnen.

**Adobe-** analyse is volledig geïntegreerd in AEM apps en maakt gedetailleerde tracering van distributie, geolocatie, besturingssystemen, apparaten, klikstreams, iBeacon-tracking en meer mogelijk.

## Apps maken {#creating-apps}

Ontwikkelaars kunnen de [AEM PhoneGap Starter Kit](https://github.com/Adobe-Marketing-Cloud/aem-phonegap-starter-kit) samen met extra bronnen in [https://github.com/adobe-marketing-cloud-apps](https://github.com/adobe-marketing-cloud-apps) gebruiken om AEM toepassingen met PhoneGap op te starten, inclusief een referentie-native app met Cordova Webviews.

De readme voor de Starter Kit Git-opslagplaats bevat een zelfstudie voor het gebruik van de startkit:

* De branding aanpassen
* Gemaakte doelstellingen van de steekproefbouw en plaatsing
* Configuratie van opslagplaats voor bronbeheer
* Installeren en implementeren in lokale of externe AEM
* Verwijderen uit AEM

>[!NOTE]
>
>De extra bron van de verwijzingsimplementatie, met inbegrip van laboratoria, kan op GitHub [hier ](https://github.com/adobe-marketing-cloud-apps) en, de &quot;keuken-goot&quot;bron [hier](https://github.com/blefebvre/aem-phonegap-kitchen-sink) worden gevonden.

## Ontwikkelen voor IOS 9 en de gastheren van HTTP {#developing-for-ios-and-http-hosts}

IOS-ontwikkelaars moeten op de hoogte zijn van een open probleem met Cordova-apps die op iOS 9 worden uitgevoerd. Deze kwestie verhindert verzoeken aan onveilige gastheren (zoals *http://localhost:4502*) worden gemaakt. Dit probleem zal worden opgelost met de komende vrijgave van cordova-ios (verbruikt door de CLI van Cordova), maar ondertussen zijn er twee oplossingen beschikbaar:

1. Als directe oplossing kunt u nog steeds alle iOS 8-simulators zonder problemen gebruiken.
1. Als u iOS 9 moet gebruiken, kunt u de toepassingen -Info.plist (gevonden na het uitvoeren van `cordova platform add ios` in &quot;&lt;app root>/platforms/ios/&lt;app name>/&lt;app name>-Info.plist&quot;) handmatig bewerken en de volgende eigenschap opnemen:

```
<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key> <true/>

</dict>
```

>[!NOTE]
>
>Voor meer informatie over &quot;de Veiligheid van het Vervoer van de app&quot;, zie de volgende sectie van [iOS9 pre-releasedocs](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW14) en dit [Stack Overflow besprekings](https://stackoverflow.com/questions/30751053/ios9-ats-what-about-html5-based-apps/).

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
* [AEM Mobile-inhoud aanpassen](/help/mobile/phonegap-aem-mobile-content-personalization.md)
* [De anatomie van een app](/help/mobile/phonegap-apps-arch.md)
* [Is uw hybride app gereed voor AEM Mobile?](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwerpen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)
