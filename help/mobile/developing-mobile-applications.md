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
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Mobiele toepassingen ontwikkelen in AEM {#developing-mobile-applications-in-aem}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

AEM maakt gebruik van Adobe PhoneGap en Adobe Publishing Solutions, waarmee u zowel content-rich als op toepassingen gebaseerde mobiele toepassingen voor meerdere platforms kunt maken en beheren:

* Beheer al uw bedrijven mobiele apps op één locatie.
* Bekijk toepassingen in ontwikkelings- en testomgevingen zonder de complexiteit van inrichtingsprofielen en de extra inspanning om uw app te maken en te uploaden voor delen.
* Gebruik de AEM ontwerpomgeving om rijke inhoud voor uw apps te maken en te beheren.
* Gebruik de HTML5 met Adobe PhoneGap om rijke ervaringen met apparaat-inheemse mogelijkheden tot stand te brengen.
* Introduceer HTML5-webweergaven tot nieuwe of reeds bestaande **native** toepassingen door Cordova WebViews.
* Maak, curseer en deel rijke multimedia-inhoud via alle leveringskanalen, waaronder web, mobiel-web, mobiele-app en drukwerk.

AEM kan worden geïntegreerd met de Adobe PhoneGap Build-service (`https://build.phonegap.com/`) om het ontwikkelings- en implementatieproces van toepassingen te vereenvoudigen.

**Adobe ContentSync** Hiermee kunnen gebruikers eenvoudig pagina- en inhoudsupdates over-the-Air (OTA) downloaden naar hun apparaten zonder dat ze de toepassing opnieuw moeten installeren of moeten downloaden van de appStore, Google Play of andere toepassingsbronnen.

**Adobe Analytics** is volledig geïntegreerd in AEM apps en maakt gedetailleerde tracering van distributie, geolocatie, besturingssystemen, apparaten, klikstreams, iBeacon-tracking en meer mogelijk.

## Apps maken {#creating-apps}

Ontwikkelaars kunnen de [AEM PhoneGap Starter-kit](https://github.com/Adobe-Marketing-Cloud/aem-phonegap-starter-kit) samen met extra bronnen gevonden in [https://github.com/adobe-marketing-cloud-apps](https://github.com/adobe-marketing-cloud-apps) om AEM toepassingen met PhoneGap op te starten, inclusief een native referentie-app met Cordova Webviews.

De readme voor de Starter Kit Git-opslagplaats bevat een zelfstudie voor het gebruik van de startkit:

* De branding aanpassen
* Gemaakte doelstellingen van de steekproefbouw en plaatsing
* Configuratie van opslagplaats voor bronbeheer
* Installeren en implementeren in lokale of externe AEM
* Verwijderen uit AEM

>[!NOTE]
>
>De extra bron van de verwijzingsimplementatie, met inbegrip van laboratoria, kan op GitHub worden gevonden [hier](https://github.com/adobe-marketing-cloud-apps) en de &quot;keukenroze&quot;-bron [hier](https://github.com/blefebvre/aem-phonegap-kitchen-sink).

## Ontwikkelen voor IOS 9 en HTTP-hosts {#developing-for-ios-and-http-hosts}

IOS-ontwikkelaars moeten op de hoogte zijn van een open probleem met Cordova-apps die op iOS 9 worden uitgevoerd. Deze kwestie verhindert verzoeken aan onveilige gastheren (zoals *http://localhost:4502*). Dit probleem zal worden opgelost met de komende vrijgave van cordova-ios (verbruikt door de CLI van Cordova), maar ondertussen zijn er twee oplossingen beschikbaar:

1. U kunt nu alle iOS 8-simulators zonder problemen gebruiken.
1. Als u iOS 9 moet gebruiken, kunt u de apps -Info.plist gebruiken (deze vindt u na uitvoering `cordova platform add ios` in &quot;&lt;app root=&quot;&quot;>/platforms/ios/&lt;app name=&quot;&quot;>/&lt;app name=&quot;&quot;>-Info.plist&quot;) kan handmatig worden bewerkt en de volgende eigenschap bevatten:

```
<key>NSAppTransportSecurity</key>

<dict>

<key>NSAllowsArbitraryLoads</key> <true/>

</dict>
```

>[!NOTE]
>
>Voor meer informatie over &quot;de Veiligheid van het Vervoer van de App&quot;, zie de volgende sectie van [Apple iOS9-prereleasedocumenten](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW14) en dit [Stapel overloop, discussie](https://stackoverflow.com/questions/30751053/ios9-ats-what-about-html5-based-apps/).

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
