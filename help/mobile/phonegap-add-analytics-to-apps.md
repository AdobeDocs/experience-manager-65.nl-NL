---
title: Adobe Analytics toevoegen aan uw mobiele toepassing
seo-title: Adobe Analytics toevoegen aan uw mobiele toepassing
description: Volg deze pagina voor meer informatie over het gebruik van Mobile App Analytics in uw AEM-toepassingen door integratie met Adobe Mobile Services.
seo-description: Volg deze pagina voor meer informatie over het gebruik van Mobile App Analytics in uw AEM-toepassingen door integratie met Adobe Mobile Services.
uuid: d3ff6f9b-0467-4abe-9a59-b3495a6af0f8
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: cd9d2bea-48d8-4a17-8544-ea25dcad69f3
translation-type: tm+mt
source-git-commit: 8279cd590244a7f2d20cfaf1c7505a3ef57fae4a
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---


# Adobe Analytics toevoegen aan uw mobiele toepassing{#add-adobe-analytics-to-your-mobile-application}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

Wilt u aantrekkelijke en relevante ervaringen opbouwen voor gebruikers van mobiele toepassingen? Als u niet de Adobe Mobile Services SDK gebruikt om de levenscyclus en het gebruik van de toepassing te controleren en te meten, dan waarop baseert u uw besluiten? Waar zijn uw meest loyale klanten? Hoe kan je garanderen dat je relevant blijft en conversies optimaliseert?

Hebben uw gebruikers toegang tot alle inhoud? Verlaten ze de app en zo ja, waar? Hoe vaak blijven ze in de app en hoe vaak komen ze terug om de app te gebruiken? Welke veranderingen kunt u introduceren en dan die verhoging behoud meten? Hoe zit het met crashsnelheden? crasht uw app voor uw gebruikers?

Profiteer van [Mobile App Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) in uw AEM-toepassingen door te integreren met [Adobe Mobile Services](https://www.adobe.com/marketing-cloud/mobile-marketing.html).

Instrueer uw AEM-apps om te volgen, rapporteren en te begrijpen hoe gebruikers omgaan met uw mobiele app en inhoud en om belangrijke levenscyclusmetriek te meten, zoals lanceringen, tijd in app en crashsnelheid.

In deze sectie wordt beschreven hoe AEM *Developers*:

* Mobiele analysemogelijkheden integreren in uw mobiele toepassing
* Test uw analyses bijhouden met Bloodhound

## Vereisten {#prerequisties}

AEM Mobile heeft een Adobe Analytics-account nodig om trackinggegevens in uw app te verzamelen en te rapporteren. Als onderdeel van de configuratie moet de AEM *Beheerder* eerst:

* Stel een Adobe Analytics-account in en maak een rapportsuite voor uw toepassing in Mobile Services.
* Configureer een AMS-Cloud Service in Adobe Experience Manager (AEM).

## Voor ontwikkelaars - Mobiele analysemogelijkheden integreren in uw app {#for-developers-integrate-mobile-analytics-into-your-app}

### Configureer ContentSync om het configuratiebestand {#configure-contentsync-to-pull-in-configuration-file} te gebruiken

Nadat het account Analytics is ingesteld, moet u een configuratie voor Content Sync maken om de inhoud in uw mobiele toepassing te plaatsen.

Zie Inhoud synchroniseren configureren voor meer informatie. De configuratie zal de Synchronisatie van de Inhoud moeten instrueren om ADBMobileConfig in de /www folder te zetten. In de Geometrixx Outdoors App vindt u bijvoorbeeld de configuratie van Content Sync: */content/phonegap/geometrixx-outdoor/shell/jcr:content/pge-app/app-config/ams-ADBMobileConfig*. Er is ook een configuratie voor ontwikkeling. het is echter identiek aan de niet-ontwikkelingsconfiguratie in het geval van Geometrixx Outdoors.

Raadpleeg Analytics - Mobile Services - Adobe Mobile Services SDK Config File voor meer informatie over het downloaden van ADBMobileConfig vanuit het dashboard voor AEM toepassingen voor mobiele.

```xml
<jcr:root xmlns:jcr="https://www.jcp.org/jcr/1.0" xmlns:nt="https://www.jcp.org/jcr/nt/1.0"
    jcr:primaryType="nt:unstructured"
    extension="json"
    path="../../../.."
    selector="ADBMobileConfig"
    targetRootDirectory="www"
    type="mobileADBMobileConfigJSON"/>
```

Voor elk platform moet ADBMobileConfig naar een specifieke locatie worden gekopieerd.

Als het bouwen met CLI PhoneGap dit met cordova kan worden gedaan bouwen hamanuscripten. Dit is te zien in de Geometrixx Outdoor App op:*content/phonegap/geometrixx-outdoors/shell/_jcr_content/pge-app/app-content/phonegap/scripts/restore_plugins.js.*

Voor iOS moet het bestand worden gekopieerd naar de map **Resources** van het XCode-project (bijv. &quot;platforms/ios/Geometrixx/Resources/ADBMobileConfig.json&quot;). Als de toepassing is bedoeld voor Android, is het pad waarnaar u wilt kopiëren &quot;platforms/android/assets/ADBMobileConfig.json&quot;. Voor meer details bij het gebruiken van haken tijdens de bouwstijl PhoneGap CLI verwijs naar [Drie haken uw Cordova/PhoneGap projectbehoeften](https://devgirl.org/2013/11/12/three-hooks-your-cordovaphonegap-project-needs/).

```xml
///////////////////////////
//          iOS
///////////////////////////
    ios : [
        {
            "www/ADBMobileConfig.json": "platforms/ios/<YOUR_APP_NAME>/Resources/ADBMobileConfig.json"
        }
    ],
///////////////////////////
//          ANDROID
///////////////////////////
    android: [
        {
            "www/ADBMobileConfig.json": "platforms/android/assets/ADBMobileConfig.json"
        }
    ]
```

### Voeg de insteekmodule AMS toe in de app {#add-the-ams-plugin-in-the-app}

Voor de app om de gegevens te verzamelen, moet de insteekmodule Adobe Mobile Services (AMS) als onderdeel van de app worden opgenomen. Door de plug-in als een functie in config.xml van de app op te nemen, kan een andere Cordova-haak worden gebruikt om de plug-in automatisch toe te voegen tijdens het PhoneGap-ontwikkelproces.

```xml
<feature name="ADBMobile">
    <param name="id" value="https://github.com/Adobe-Marketing-Cloud/mobile-services#0482f9cedf90c98a8d4b07219ece1933b2e46a60"/>
</feature>
```

De Geometrixx Outdoors App config.xml bevindt zich op */content/phonegap/geometrixx-outdoor/shell/jcr:content/pge-app/app-content/phonegap/www/config.xml*. In het bovenstaande voorbeeld wordt een specifieke versie van de insteekmodule gevraagd die moet worden gebruikt door een &#39;#&#39; en een tagwaarde toe te voegen na de insteekmodule-URL. Dit is een goede gewoonte om ervoor te zorgen dat onverwachte problemen zich niet voordoen als gevolg van het toevoegen van niet-geteste plug-ins tijdens een build.

Nadat u deze stappen hebt uitgevoerd, wordt uw app ingeschakeld om alle levenscyclusmetriek te rapporteren die door Adobe Analytics zijn verschaft. Dit omvat gegevens zoals lanceringen, neerstortingen en installaties. Als dat de enige gegevens zijn waar je om geeft, dan ben je klaar. Als u aangepaste gegevens wilt verzamelen, moet u deze coderen.

### Instrueer uw code voor het volledig bijhouden van de app {#instrument-your-code-for-full-app-tracking}

Er zijn verschillende tracking-API&#39;s beschikbaar in de [AMS Phonegap-insteekmodule-API.](https://docs.adobe.com/content/help/en/mobile-services/ios/phonegap-ios/phonegap-methods.html)

Hiermee kunt u staten en handelingen bijhouden, zoals waar de pagina&#39;s waarnaar uw gebruikers navigeren in uw app, waarin de besturingselementen het meest worden gebruikt. De eenvoudigste manier om uw app voor tracering te gebruiken, is om gebruik te maken van de API&#39;s voor Analytics die door de AMS-plug-in worden geleverd.

* ADB.trackState()
* ADB.trackAction()

Ter referentie kunt u de code in de app Geometrixx Outdoors bekijken. In de app Geometrixx Outdoors worden alle paginanavigaties bijgehouden met behulp van de methode ADB.trackState(). Zie voor meer informatie de broncode voor /libs/mobileapps/components/angular/ng-page/clientlibs/app-navigation.js

Door uw broncode met deze methodevraag van instrumenten te voorzien kunt u volledige metriek tegen uw toepassing verzamelen.

#### Eigenschappen voor het verbinden met AMS {#properties-for-connecting-to-ams}

*com.adobe.cq.mobile.mobileservices.impl.service.* MobileServicesHttpClientImpl stelt de volgende eigenschappen voor het verbinden met AMS beschikbaar:

| **Label** | **Beschrijving** | **Standaard** |
|---|---|---|
| API-eindpunt | De basis-URL van de HTTP-API&#39;s van Adobe Mobile Services | https://api.omniture.com |
| Config-eindpunt | De URL die wordt gebruikt om ADB Mobile Config voor bepaalde rapportsuite-id op te halen | /ams/1.0/app/config/ |
| Mobiele service-apps | Een lijst met apps ophalen in het gebruikersbedrijf | /ams/1.0/apps |

