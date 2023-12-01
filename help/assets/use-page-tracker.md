---
title: Paginanummering gebruiken en code insluiten in webpagina's
description: Leer hoe u JavaScript-codes in uw websitecode kunt opnemen in Paginanummering en hoe u JavaScript-codes kunt insluiten om Adobe Analytics in staat te stellen gebruiksgegevens vast te leggen rond elementen.
contentOwner: AG
role: Architect, Admin
feature: Asset Reports
exl-id: 14d02015-df00-4566-a098-de76eaf42605
source-git-commit: 5e56441d2dc9b280547c91def8d971e7b1dfcfe3
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Paginatracering gebruiken en code insluiten in webpagina&#39;s {#using-page-tracker-and-embed-code-in-web-pages}

Paginanummering is een stuk JavaScript-code dat u in code van externe websites opneemt, zodat Adobe Analytics gebruiksgegevens kan vastleggen rond [!DNL Adobe Experience Manager Assets] op deze websites.

Als u gebeurtenissen wilt vastleggen die specifiek zijn voor elementen, zoals klikken, neemt u ook de code Insluiten op in de code van websites van derden.

De volgende voorbeeldcode toont hoe een webpagina die zowel de code van Paginanummer als de code van Insluiten bevat eruitziet:

```html
<!DOCTYPE html>
<html>
    <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in milliseconds
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","xxxx","xxx","list1","eVar3","event8","event7");
            </script>

    </head>

    <body>

                                <img
            src="https://10.41.52.147:4502/xxxx/content/dam/test/abc.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
                <img
                    src="http://localhost/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
</html>
```

## Code voor paginatracering toevoegen {#adding-page-tracker-code}

U voegt de code van de paginacontracker binnen de kopbalsectie van uw websitecode toe. Het volgende codefragment toont de code van de Tracker van de Pagina inbegrepen in een steekproefWeb-pagina:

```xml
 <head>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/sitecatalyst/appmeasurement.js"></script>
            <script type="text/javascript" src="http://localhost:4502/xxxx/etc.clientlibs/dam/clientlibs/foundation/assetinsights/pagetracker.js"></script>
            <script type="text/javascript">
                                assetAnalytics.attrTrackable = 'trackable';
                assetAnalytics.defaultTrackable = false;
                assetAnalytics.attrAssetID = 'aem-asset-id';
                assetAnalytics.assetImpressionPollInterval = 200; // interval in millis
                assetAnalytics.charsLimitForGET = 2000; // bytes
                assetAnalytics.dispatcher.init("assetstesting","abc.net","bee","list1","eVar3","event8","event7");
            </script>

 </head>
```

## Insluitcode toevoegen {#add-embed-code}

U voegt de insluitcode toe aan de hoofdtekst van de websitecode. In het volgende codefragment wordt de insluitcode weergegeven die in een voorbeeldwebpagina is opgenomen:

```xml
<body>

      <img
            src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
            data-aem-asset-id="aaid:a386f2cd78234becb66bd11575f9452d"
            data-trackable=true
            onload=assetAnalytics.core.assetLoaded(this)>

        <a
            href="https://www.adobe.com"

            onclick="assetAnalytics.core.assetClicked(this);return false">
           <img
                    src="http://localhost:4502/xxxx/content/dam/test/xyz.jpg"
                    data-aem-asset-id="aaid:7fa01fce0ebe40268cd6dcf07e2d9cb1"
                    data-trackable=true
                    onload=assetAnalytics.core.assetLoaded(this)>
        </a>

    </body>
```
