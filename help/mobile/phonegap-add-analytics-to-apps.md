---
title: Adobe Analytics toevoegen aan uw mobiele toepassing
description: Volg deze pagina voor meer informatie over het gebruik van Mobile App Analytics in uw Adobe Experience Manager-toepassingen door integratie met Adobe Mobile Services.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: 8d965e94-c368-481d-b000-6e22456c34db
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '904'
ht-degree: 0%

---

# Adobe Analytics toevoegen aan uw mobiele toepassing{#add-adobe-analytics-to-your-mobile-application}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

Wilt u aantrekkelijke en relevante ervaringen opbouwen voor gebruikers van mobiele toepassingen? Als u niet de Adobe Mobiele Diensten SDK gebruikt om toepassingslevenscyclus en gebruik te controleren en te meten, dan op wat baseert u uw besluiten? Waar zijn uw meest loyale klanten? Hoe kunt u ervoor zorgen u relevant blijft en omzettingen optimaliseert?

Hebben uw gebruikers toegang tot alle inhoud? Verlaten ze de app en zo ja, waar? Hoe vaak blijven ze in de app en hoe vaak komen ze terug om de app te gebruiken? Welke veranderingen kunt u introduceren en dan die verhoging behoud meten? Hoe zit het met crashsnelheden? crasht uw app voor uw gebruikers?

Profiteer van [Mobiele App Analytics](https://business.adobe.com/products/analytics/mobile-marketing.html) in uw Adobe Experience Manager-toepassingen (AEM) door integratie met [Adobe mobiele services](https://business.adobe.com/products/campaign/mobile-marketing.html).

Instrueer uw AEM-apps om te volgen, rapporteren en te begrijpen hoe uw gebruikers omgaan met uw mobiele app en inhoud en om belangrijke levenscyclusmetriek te meten, zoals lanceringen, tijd in app en crashsnelheid.

In deze sectie wordt beschreven hoe AEM *Ontwikkelaars* kan:

* Mobiele analysemogelijkheden integreren in uw mobiele toepassing
* Test uw analyses bijhouden met Bloodhound

## Vereisten {#prerequisties}

AEM Mobile heeft een Adobe Analytics-account nodig om trackinggegevens in uw app te verzamelen en te rapporteren. Als onderdeel van de configuratie, AEM *Beheerder* moet eerst:

* Stel een Adobe Analytics-account in en maak een rapportsuite voor uw toepassing in Mobile Services.
* Een AMS-Cloud Service configureren in Adobe Experience Manager (AEM).

## Voor ontwikkelaars - Mobiele analysemogelijkheden integreren in uw app {#for-developers-integrate-mobile-analytics-into-your-app}

### Configureer ContentSync om het configuratiebestand te gebruiken {#configure-contentsync-to-pull-in-configuration-file}

Nadat de account Analytics is ingesteld, maakt u een configuratie voor inhoudssynchronisatie om de inhoud in uw mobiele toepassing te plaatsen.

Zie Inhoud synchroniseren met inhoud configureren voor meer informatie. De configuratie moet de Synchronisatie van de Inhoud opdragen om ADBMobileConfig in de /www folder te zetten. In de Geometrixx Outdoors-app is de configuratie van Content Sync bijvoorbeeld ingesteld op: */content/phonegap/geometrixx-outdoor/shell/jcr:content/pge-app/app-config/ams-ADBMobileConfig*. Er is ook een configuratie voor ontwikkeling. Nochtans, is het identiek aan de niet-ontwikkelingsconfiguratie als er Geometrixx Outdoors zijn.

Zie Analytics - Mobile Services - Adobe Mobile Services SDK Config File voor meer informatie over het downloaden van ADBMobileConfig vanuit het dashboard voor toepassingen voor mobiele toepassingen AEM toepassingen.

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

Voor iOS moet het bestand naar het XCode-project worden gekopieerd **Bronnen** directory (bijvoorbeeld &quot;platforms/ios/Geometrixx/Resources/ADBMobileConfig.json&quot;). Als de toepassing is bedoeld voor Android™, is het pad naar kopiëren &quot;platforms/android/assets/ADBMobileConfig.json&quot;. Voor meer details bij het gebruiken van haken tijdens CLI van PhoneGap bouwt, zie [Drie haken voor uw Cordova/PhoneGap-project](https://gist.github.com/jlcarvalho/22402d013bc72f795d45a01836ce735c).

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

### De AMS-plug-in toevoegen in de app {#add-the-ams-plugin-in-the-app}

Voor de app om de gegevens te verzamelen, moet de insteekmodule Adobe Mobile Services (AMS) als onderdeel van de app worden opgenomen. Door de plug-in als een functie in config.xml van de app op te nemen, kan een andere Cordova-haak worden gebruikt om de plug-in automatisch toe te voegen tijdens het PhoneGap-ontwikkelproces.

```xml
<feature name="ADBMobile">
    <param name="id" value="https://github.com/Adobe-Marketing-Cloud/mobile-services#0482f9cedf90c98a8d4b07219ece1933b2e46a60"/>
</feature>
```

De Geometrixx Outdoors App config.xml wordt gevestigd bij */content/phonegap/geometrixx-outdoor/shell/jcr:content/pge-app/app-content/phonegap/www/config.xml*. In het bovenstaande voorbeeld wordt een specifieke versie van de insteekmodule gevraagd die moet worden gebruikt door een &#39;#&#39; en een tagwaarde toe te voegen na de insteekmodule-URL. Dit is een goede manier om ervoor te zorgen dat er geen onverwachte problemen optreden omdat niet-geteste plug-ins tijdens een build worden toegevoegd.

Nadat u deze stappen hebt uitgevoerd, wordt uw app ingeschakeld om alle levenscyclusmetriek te rapporteren die Adobe Analytics biedt. Dit omvat gegevens zoals lanceringen, neerstortingen en installaties. Als dat de enige gegevens zijn waar je om geeft, dan ben je klaar. Als u douanegegevens wilt verzamelen, dan moet u uw code instrumenten.

### Instrueer uw code voor volledige toepassingsspatiëring {#instrument-your-code-for-full-app-tracking}

Er zijn verschillende tracking-API&#39;s beschikbaar in het dialoogvenster [API voor insteekmodule AMS Phonegap](https://github.com/Adobe-Marketing-Cloud/mobile-services/blob/master/docs/ios/phonegap/phonegap-methods.md)

Hiermee kunt u staten en handelingen bijhouden, zoals waar de pagina&#39;s waarnaar uw gebruikers navigeren in uw app, waarin de besturingselementen het meest worden gebruikt. De gemakkelijkste manier om uw app voor tracering te gebruiken, is met behulp van de API&#39;s voor Analytics die door de AMS-plug-in worden geleverd.

* ADB.trackState()
* ADB.trackAction()

Zie ter referentie de code in de app Geometrixx Outdoors. In de app Geometrixx Outdoors wordt alle paginanavigatie bijgehouden met behulp van de methode ADB.trackState(). Zie de broncode voor /libs/mobileapps/components/angular/ng-page/clientlibs/app-navigation.js voor meer informatie.

Door van instrumenten de broncode met deze methodevraag te voorzien, kunt u volledige metriek tegen uw toepassing verzamelen.

#### Eigenschappen voor het verbinden met AMS {#properties-for-connecting-to-ams}

*com.adobe.cq.mobile.mobileservices.impl.service.MobileServicesHttpClientImp* l stelt de volgende eigenschappen voor het verbinden met AMS bloot:

| **Label** | **Beschrijving** | **Standaard** |
|---|---|---|
| API-eindpunt | De basis-URL van de HTTP-API&#39;s van de Adobe Mobile Services | https://api.omniture.com |
| Config-eindpunt | De URL die wordt gebruikt om ADB Mobile Config voor bepaalde rapportsuite-id op te halen | /ams/1.0/app/config/ |
| Mobiele service-apps | Een lijst met apps ophalen in het gebruikersbedrijf | /ams/1.0/apps |
