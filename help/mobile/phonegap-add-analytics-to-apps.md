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
source-git-commit: 70b18dbe351901abb333d491dd06a6c1c1c569d6
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---


# Adobe Analytics toevoegen aan uw mobiele toepassing{#add-adobe-analytics-to-your-mobile-application}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Wilt u aantrekkelijke en relevante ervaringen opbouwen voor gebruikers van mobiele toepassingen? Als u de SDK van Adobe Mobile Services niet gebruikt om de levenscyclus en het gebruik van toepassingen te controleren en te meten, waarop baseert u uw beslissingen? Waar zijn uw meest loyale klanten? Hoe kan je garanderen dat je relevant blijft en conversies optimaliseert?

Hebben uw gebruikers toegang tot alle inhoud? Verlaten ze de app en zo ja, waar? Hoe vaak blijven ze in de app en hoe vaak komen ze terug om de app te gebruiken? Welke veranderingen kunt u introduceren en dan die verhoging behoud meten? Hoe zit het met crashsnelheden? crasht uw app voor uw gebruikers?

Profiteer van [Mobile App Analytics](https://www.adobe.com/ca/solutions/digital-analytics/mobile-web-apps-analytics.html) in uw AEM-apps door deze te integreren met [Adobe Mobile Services](https://www.adobe.com/marketing-cloud/mobile-marketing.html).

Instrueer uw AEM-toepassingen om te volgen, rapporteren en te begrijpen hoe gebruikers omgaan met uw mobiele app en inhoud en om belangrijke levenscyclusmetriek zoals lanceringen, tijd in app en crashsnelheid te meten.

In deze sectie wordt beschreven hoe AEM- *ontwikkelaars* :

* Mobiele Analytics integreren in uw mobiele toepassing
* Test uw analyses bijhouden met Bloodhound

## Vereisten {#prerequisties}

AEM Mobile heeft een Adobe Analytics-account nodig om trackinggegevens in uw app te verzamelen en te rapporteren. Als deel van de configuratie zal de *Beheerder* AEM eerst moeten:

* Stel een Adobe Analytics-account in en maak een rapportsuite voor uw toepassing in Mobile Services.
* Configureer een AMS-Cloud Service in Adobe Experience Manager (AEM).

## Voor ontwikkelaars - Mobiele Analytics integreren in uw app {#for-developers-integrate-mobile-analytics-into-your-app}

### ContentSync configureren om het configuratiebestand te gebruiken {#configure-contentsync-to-pull-in-configuration-file}

Nadat u het Analytics-account hebt ingesteld, moet u een configuratie voor inhoudssynchronisatie maken om de inhoud in uw mobiele toepassing te plaatsen.

Zie Inhoud synchroniseren configureren voor meer informatie. De configuratie zal de Synchronisatie van de Inhoud moeten instrueren om ADBMobileConfig in de /www folder te zetten. In de Buiten-app Geometrixx vindt u bijvoorbeeld de configuratie van Content Sync bij: */content/phonegap/geometrixx-outdoor/shell/jcr:content/pge-app/app-config/ams-ADBMobileConfig*. Er is ook een configuratie voor ontwikkeling. in het geval van Geometrixx Outdoor is de configuratie echter identiek aan de configuratie zonder ontwikkeling.

Raadpleeg het configuratiebestand van Analytics - Mobile Services - Adobe Mobile Services SDK voor meer informatie over het downloaden van ADBMobileConfig vanaf het dashboard voor AEM-toepassingen voor mobiele toepassingen.

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

Voor iOS moet het bestand worden gekopieerd naar de map **Resources** (bijv. &quot;platforms/ios/Geometrixx/Resources/ADBMobileConfig.json&quot;). Als de toepassing is bedoeld voor Android, is het pad waarnaar u wilt kopiëren &quot;platforms/android/assets/ADBMobileConfig.json&quot;. Voor verdere details bij het gebruiken van haken tijdens de bouwstijl PhoneGap CLI verwijs naar [Drie haken uw Cordova/het projectbehoeften](https://devgirl.org/2013/11/12/three-hooks-your-cordovaphonegap-project-needs/)van PhoneGap.

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

De toepassing kan de gegevens alleen verzamelen als de insteekmodule Adobe Mobile Services (AMS) is opgenomen in de app. Door de plug-in als een functie in config.xml van de app op te nemen, kan een andere Cordova-haak worden gebruikt om de plug-in automatisch toe te voegen tijdens het PhoneGap-ontwikkelproces.

```xml
<feature name="ADBMobile">
    <param name="id" value="https://github.com/Adobe-Marketing-Cloud/mobile-services#0482f9cedf90c98a8d4b07219ece1933b2e46a60"/>
</feature>
```

Het bestand Geometrixx Outdoor App config.xml bevindt zich op de locatie */content/phonegap/geometrixx-outdoor/shell/jcr:content/pge-app/app-content/phonegap/www/config.xml*. In het bovenstaande voorbeeld wordt een specifieke versie van de insteekmodule gevraagd die moet worden gebruikt door een &#39;#&#39; en een tagwaarde toe te voegen na de insteekmodule-URL. Dit is een goede gewoonte om ervoor te zorgen dat onverwachte problemen zich niet voordoen als gevolg van het toevoegen van niet-geteste plug-ins tijdens een build.

Nadat u deze stappen hebt uitgevoerd, wordt uw app ingeschakeld om alle levenscyclusmetriek te rapporteren die door Adobe Analytics zijn verschaft. Dit omvat gegevens zoals lanceringen, neerstortingen en installaties. Als dat de enige gegevens zijn waar je om geeft, dan ben je klaar. Als u aangepaste gegevens wilt verzamelen, moet u deze coderen.

### Instrueer uw code voor het volledig bijhouden van de app {#instrument-your-code-for-full-app-tracking}

Er zijn verschillende tracking-API&#39;s beschikbaar in de [AMS Phonegap-insteekmodule.](https://docs.adobe.com/content/help/en/mobile-services/ios/phonegap-ios/phonegap-methods.html)

Hiermee kunt u staten en handelingen bijhouden, zoals waar de pagina&#39;s waarnaar uw gebruikers navigeren in uw app, waarin de besturingselementen het meest worden gebruikt. De eenvoudigste manier om uw toepassing voor tracering te gebruiken, is om gebruik te maken van de Analytics API&#39;s die door de AMS-plug-in worden geleverd.

* ADB.trackState()
* ADB.trackAction()

Ter referentie kunt u de code in de Geometrixx-app Buiten bekijken. In de toepassing Geometrixx Outdoor worden alle paginanavigaties bijgehouden met behulp van de methode ADB.trackState(). Zie voor meer informatie de broncode voor /libs/mobileapps/components/angular/ng-page/clientlibs/app-navigation.js

Door uw broncode met deze methodevraag van instrumenten te voorzien kunt u volledige metriek tegen uw toepassing verzamelen.

### Het testen van Analytics-tracking met Bloodhound  {#testing-analytics-tracking-with-bloodhound}

![](do-not-localize/chlimage_1.jpeg)

<!--NOTE TO WRITER: Bloodhound is no longer available.-->

U kunt desgewenst vóór de implementatie naar productie de Adobe-tool [Bloodhound](https://marketing.adobe.com/developer/gallery/bloodhound-app-measurement-qa-tool-1) gebruiken om de configuratie van de analysemogelijkheden te testen. Als u de analyseconfiguratie wilt testen, moet u het bestand ADBMobileConfig.json bewerken om te wijzen naar de server waarop Bloodhound wordt uitgevoerd in plaats van naar de Analytics-server. Om deze verandering aan te brengen, van uw ADBMobileConfig.json verander de volgende ingang.

```xml
...
"analytics": {
    "rsids": "YOUR_RSID",
    "server": "YOUR_TRACKING_SERVER:YOUR_TRACKING_PORT",
...
```

Wijzigen om aan te passen aan dit item:

```xml
...
"analytics": {
    "rsids": "YOUR_RSID",
    "server": "localhost:50000",
...
```

Hiermee worden alle gegevens die door de AMS-plug-in zijn verzameld, omgeleid naar Bloodhound, zodat u de resultaten kunt bekijken.

#### Eigenschappen voor het verbinden met AMS {#properties-for-connecting-to-ams}

*com.adobe.cq.mobile.mobileservices.impl.service.* MobileServicesHttpClientImpl stelt de volgende eigenschappen voor het verbinden met AMS beschikbaar:

| **Label** | **Beschrijving** | **Standaard** |
|---|---|---|
| API-eindpunt | De basis-URL van de HTTP-API&#39;s van Adobe Mobile Services | https://api.omniture.com |
| Config-eindpunt | De URL die wordt gebruikt om ADB Mobile Config voor bepaalde rapportsuite-id op te halen | /ams/1.0/app/config/ |
| Mobiele service-apps | Een lijst met apps ophalen in het gebruikersbedrijf | /ams/1.0/apps |

