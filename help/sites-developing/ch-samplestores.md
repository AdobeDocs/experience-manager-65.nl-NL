---
title: Voorbeeld van ContextHub Store-kandidaten
description: ContextHub verstrekt verscheidene kandidaten van de steekproefopslag die u in uw oplossingen kunt gebruiken
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: d8d9a799-3e30-442a-843b-d4d7ba70c557
solution: Experience Manager, Experience Manager Sites
feature: Developing,Personalization
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 1%

---

# Voorbeeld van ContextHub Store-kandidaten{#sample-contexthub-store-candidates}

ContextHub verstrekt verscheidene kandidaten van de steekproefopslag die u in uw oplossingen kunt gebruiken. Voor elk monster wordt de volgende informatie verstrekt:

* Waar u de broncode kunt vinden, zodat u deze kunt openen voor leerdoeleinden.
* Hoe te om de opslag te vormen die u van de opslagkandidaten creeert.
* Hoe de opslaggegevens zijn gestructureerd zodat u er toegang toe hebt.

>[!WARNING]
>
>De kandidaten van de steekproefopslag worden verstrekt als verwijzingsconfiguraties om u te helpen uw eigen specifieke configuratie voor uw project bouwen. Niet direct gebruiken.

## aem.segmentation Voorbeeld Store Candidate {#aem-segmentation-sample-store-candidate}

Bewaren voor opgeloste en onopgeloste segmenten ContextHub. Wint automatisch segmenten van ContextHub SegmentManager terug.

### Source-locatie {#source-location-segmentation}

`/libs/settings/cloudsettings/legacy/contexthub/segmentation`

### Basisimplementatie {#base-implementation-segmentation}

De opslagkandidaat aem.segmentation breidt [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore) uit.

### Configuratie {#configuration-segmentation}

Wanneer u een opslag aem.segmentation creeert, te hoeven u niet om een gedetailleerde configuratie te verstrekken. De standaardconfiguratie specificeert de plaats van de ContextHub segmentdefinities.

```xml
{
   "service":{
      "jsonp":false,
      "timeout":1000,
      "path":"/etc/segmentation/contexthub.segment.js"
   }
}
```

## contexthub.geolocation Sample Store Candidate {#contexthub-geolocation-sample-store-candidate}

De voorbeeldopslagkandidaat contextthub.geolocation gebruikt Google Maps om informatie over de cliëntplaats te verkrijgen en op te slaan.

### Source-locatie {#source-location-geolocation}

`/libs/settings/cloudsettings/legacy/contexthub/geolocation`

### Basisimplementatie {#base-implementation-geolocation}

De kandidate contextthub.geolocationStore breidt [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore) uit.

### Configuratie {#configuration-geolocation}

In de standaardconfiguratie wordt informatie opgegeven over de Google-service en de initiële breedte- en lengtecoördinaten.

```xml
{
        "service": {
            "jsonp": false,
            "timeout": 1000,
            "ttl": 1800000,
            "secure": false,
            "host": "maps.googleapis.com",
            "port": 80,
            "path": "/maps/api/geocode/json"
        },

        "eventDeferring": 16,

        "html5coordinatesDiscoveryAPI": {
            "timeout": 30000,
            "ttl": 900000,
            "highAccuracy": false
        },

        "initialValues": {
            "latitude": 37.331375,
            "longitude": -121.893992
        }
    }
```

### Gegevensposten {#data-items-geolocation}

De opslag gebruikt een gegevensboom die aan het volgende voorbeeld gelijkaardig is:

```xml
{
   "latitude":"37.331375",
   "longitude":"-121.893992"
}
```

>[!NOTE]
>
>Een veiligheidsbeleid dat in Chrome 50.x wordt geïntroduceerd vereist dat alle aan geolocatie gerelateerde vraag over een beveiligde verbinding wordt gemaakt. AEM forceert daarom https-gebruik voor geolocatie-API-aanroepen als AEM ook over https wordt uitgevoerd. Anders wordt http gebruikt om te voldoen aan het beleid van dezelfde oorsprong. Zie [ dit Google blogbericht ](https://developers.google.com/web/updates/2016/04/geolocation-on-secure-contexts-only) voor meer details over de verandering in Chrome.

## contexthub.surferinfo Sample Store Candidate {#contexthub-surferinfo-sample-store-candidate}

Hiermee slaat u informatie op over de huidige clientomgeving, zoals het apparaat, het venster, de browser, de datum en het tijdstip.

### Source-locatie {#source-location-surferinfo}

`/libs/settings/cloudsettings/legacy/contexthub/surferinfo`

### Basisimplementatie {#base-implementation-surferinfo}

De kandidaat van de contexthub.datetime store is [`ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore) uitgebreid.

### Configuratie {#configuration-surferinfo}

De standaardconfiguratie wordt overgeërfd van `ContextHub.Store.PersistedStore`.

### Gegevensposten {#data-items-surferinfo}

De opslag die deze opslagkandidaat gebruikt heeft een gegevensboom die aan het volgende voorbeeld gelijkaardig is:

```xml
{
   "display":{
      "resolution":{
         "width":1440,
         "height":900
      },
      "devicePixelRatio":1,
      "colorDepth":24,
      "nrOfColors":16777216,
      "pixelsPerInch":96,
      "orientation":{
         "mode":"landscape",
         "direction":"normal"
      }
   },
   "window":{
      "dimension":{
         "width":1395,
         "height":652
      },
      "percentageUsage":0.7
   },
   "browser":{
      "version":"39.0",
      "family":"Firefox",
      "userAgent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:39.0) Gecko/20100101 Firefox/39.0"
   },
   "device":{
      "category":"Desktop",
      "type":"Desktop",
      "model":"PC",
      "version":""
   },
   "isMobile":true,
   "os":{
      "name":"Mac OS X",
      "version":"10"
   },
   "year":2015,
   "month":7,
   "day":22,
   "hour":14,
   "minutes":1
}
```

## graniet.emulators Sample Store Candidate {#granite-emulators-sample-store-candidate}

De granite.emulators steekproefopslagkandidaat slaat informatie over cliëntapparaten op.

### Source-locatie {#source-location-emulators}

`/libs/settings/cloudsettings/legacy/contexthub/emulators`

### Basisimplementatie {#base-implementation-emulators}

De kandidate contextthub.geolocationStore breidt [`ContextHub.Store.PersistedStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore) uit.

### Configuratie {#configuration-emulators}

De standaardconfiguratie bevat een array met de naam `defaultEmulators` die informatie over verschillende apparaten bevat. Wanneer u een opslag creeert, verstrek verschillende apparatenprofielen in het bezit van de Configuratie van het Detail zoals vereist, gebruikend het formaat dat in het volgende voorbeeld wordt geïllustreerd:

```xml
{
   "defaultEmulators":[
        {
            "id": "iphone-6",
            "title": "iPhone 6",
            "type": "mobile",
            "platform": "iOS",
            "platformVersion": "8.1.3",
            "width": 750,
            "height": 1334,
            "canRotate": true,
            "orientation": "Portrait",
            "device-pixel-ratio": 2
        },
        {
            "id": "iphone-6-plus",
            "title": "iPhone 6 Plus",
            "type": "mobile",
            "platform": "iOS",
            "platformVersion": "8.1.3",
            "width": 1080,
            "height": 1920,
            "canRotate": true,
            "orientation": "Portrait",
            "device-pixel-ratio": 3
        },
        {
            "id": "galaxy-s4",
            "title": "Samsung Galaxy S4",
            "type": "mobile",
            "platform": "Android",
            "platformVersion": "4.4.2 KitKat",
            "width": 1080,
            "height": 1920,
            "canRotate": true,
            "orientation": "Portrait",
            "device-pixel-ratio": 3
        }
    ]
}
```

### Gegevensposten {#data-items-emulators}

De structuur met opslaggegevens is vergelijkbaar met het volgende voorbeeld:

```xml
{
   "devices":[
      {"id":"native",
      "title":"Native",
      "type":"screen",
      "width":1395,
      "height":374,
      "orientation":"Landscape",
      "platform":"Mac OS X",
      "platformVersion":"10",
      "canRotate":false
      },
      {"id":"ipad-3",
      "title":"iPad 3 / 4 / Air",
      "type":"tablet",
      "platform":"iOS",
      "platformVersion":"8.1.3",
      "width":1536,
      "height":2048,
      "canRotate":true,
      "orientation":"Portrait",
      "device-pixel-ratio":2
      },
      {"id":"iphone-6",
      "title":"iPhone 6",
      "type":"mobile",
      "platform":"iOS",
      "platformVersion":"8.1.3",
      "width":750,
      "height":1334,
      "canRotate":true,
      "orientation":"Portrait",
      "device-pixel-ratio":2
      },
      {"id":"galaxy-s4",
      "title":"Samsung Galaxy S4",
      "type":"mobile",
      "platform":"Android",
      "platformVersion":"4.4.2 KitKat",
      "width":1080,
      "height":1920,
      "canRotate":true,
      "orientation":"Portrait",
      "device-pixel-ratio":3
      }
   ],
   "currentDeviceId":"native",
   "orientations":[
      {"id":"landscape",
      "title":"Landscape"
      },
      {"id":"portrait",
       "title":"Portrait"
      }
   ],
   "currentDevice":{
      "id":"native",
      "title":"Native",
      "type":"screen",
      "width":1395,
      "height":374,
      "orientation":"Landscape",
      "platform":"Mac OS X",
      "platformVersion":"10",
      "canRotate":false
   }
}
```

## granite.profile Voorbeeld van winkel Kandidaat {#granite-profile-sample-store-candidate}

Hiermee worden gegevens over de huidige gebruiker opgeslagen.

### Source-locatie {#source-location-profile}

`/libs/settings/cloudsettings/legacy/contexthub/profile`

### Basisimplementatie {#base-implementation-profile}

De kandidaat van de contexthub.datetime store is [`ContextHub.Store.PersistedJSONPStore`](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore) uitgebreid.

### Configuratie {#configuration-profile}

De volgende standaardconfiguratie wordt gebruikt. Wijzig deze configuratie niet.

```xml
{
   "service":{
      "jsonp":false,
      "timeout":1000,
      "path":"${contexthub:/store/profile/path}.infinity.json"
   },
   "initialValues":{"path":"/home/users/a/anonymous"}
}
```

### Gegevensposten {#data-items-profile}

De opslag die deze opslagkandidaat gebruikt heeft een gegevensboom die aan het volgende voorbeeld gelijkaardig is:

```xml
{
   "displayName":"anonymous",
   "path":"/home/users/6/6zavE_DGre6Ad9Y5E0Ba",
   "avatar":"/etc/designs/default/images/social/avatar.png",
   "authorizableId":"anonymous"
}
```
