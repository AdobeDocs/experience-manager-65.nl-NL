---
title: Analyse met externe providers
description: Leer hoe te om uw eigen instantie van de Generische Fragmenten van Analytics te vormen om een nieuwe de dienstconfiguratie te bepalen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 9bf818f9-6e33-4557-b2e4-b0d4900f2a05
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# Analyse met externe providers {#analytics-with-external-providers}

Analyses kunnen u belangrijke en interessante informatie geven over het gebruik van uw website.

Verschillende configuraties buiten de box zijn beschikbaar voor integratie met de juiste service, bijvoorbeeld:

* [Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* [Adobe Target](/help/sites-administering/target.md)

U kunt uw eigen instantie van de **Algemene Fragmenten van Analytics** ook vormen om een nieuwe de dienstconfiguratie te bepalen.

De informatie wordt vervolgens verzameld door kleine codefragmenten die aan de webpagina&#39;s worden toegevoegd. Bijvoorbeeld:

>[!CAUTION]
>
>Scripts niet opnemen in `script` -tags.

```
var _gaq = _gaq || [];
_gaq.push(['_setAccount', 'UA-XXXXX-X']);
_gaq.push(['_trackPageview']);

(function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'https://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
})();
```

Met dergelijke fragmenten kunnen gegevens worden verzameld en rapporten worden gegenereerd. De werkelijk verzamelde gegevens zijn afhankelijk van de provider en het gebruikte codefragment. Voorbeelden van statistieken zijn:

* hoeveel bezoekers in de loop der tijd
* hoeveel pagina&#39;s zijn bezocht
* zoektermen gebruikt
* landingspagina&#39;s

>[!CAUTION]
>
>De demo-site Geometrixx-buiten is zo geconfigureerd dat de kenmerken in de Pagina-eigenschappen worden toegevoegd aan de HTML-broncode (net boven de `</html>` eindtag) in het bijbehorende `js` -script.
>
>Als uw eigen `/apps` niet overerft van de standaardpagina-component ( `/libs/foundation/components/page` ), moet u (of uw ontwikkelaars) ervoor zorgen dat de bijbehorende `js` -scripts worden opgenomen, bijvoorbeeld door `cq/cloudserviceconfigs/components/servicescomponents` op te nemen of door een vergelijkbaar mechanisme te gebruiken.
>
>Zonder dit, zal geen van de diensten (Generic, Analytics, Doel, etc.) werken.

## Een service maken met een algemeen fragment {#creating-a-new-service-with-a-generic-snippet}

Voor de basisconfiguratie:

1. Open de **console van Hulpmiddelen**.
1. Van de linkerruit, breid **Configuraties van Cloud Servicen** uit.
1. Dubbelklik **Generic Fragment van Analytics** om de pagina te openen:

   ![ Generic Fragment van Analytics ](assets/analytics_genericoverview.png)

1. Klik + om een nieuwe configuratie toe te voegen gebruikend de dialoogdoos. Wijs ten minste een naam toe, bijvoorbeeld Googles Analytics:

   ![ creeer configuratie ](assets/analytics_addconfig.png)

1. Klik **creëren**, opent de fragmentdialoog onmiddellijk - kleef het aangewezen fragment van JavaScript in het gebied:

   ![ Uitgevend de component ](assets/analytics_snippet.png)

1. Klik **O.K.** om te bewaren.

## Uw nieuwe service op pagina&#39;s gebruiken {#using-your-new-service-on-pages}

Nadat u de de dienstconfiguratie hebt gecreeerd, moet u de vereiste pagina&#39;s vormen om het te gebruiken:

1. Ga naar de pagina.
1. Open de **Eigenschappen van de Pagina** van sidekick, toen de **Cloud Servicen** tabel.
1. Klik **toevoegen de Dienst**, dan selecteren de vereiste dienst. Bijvoorbeeld, het **Algemene Fragment van Analytics**:

   ![ Toevoegend de wolkendienst ](assets/analytics_selectservice.png)

1. Klik **O.K.** om te bewaren.
1. U bent teruggekeerd aan de **Cloud Servicen** tabel. Het **Algemene Fragment van Analytics** is nu vermeld met het bericht `Configuration reference missing`. Gebruik de drop-down lijst om uw specifiek de dienstgeval te selecteren. Voorbeeld: google-analytics:

   ![ Toevoegend de configuratie van de wolkendienst ](assets/analytics_selectspecificservice.png)

1. Klik **O.K.** om te bewaren.

   Het fragment kan nu worden weergegeven als u Pagina-Source voor de pagina bekijkt.

   Nadat een hoeveelheid tijd is verstreken, kunt u de verzamelde statistieken bekijken.

   >[!NOTE]
   >
   >Als de configuratie aan een pagina in bijlage is die kindpagina&#39;s heeft, wordt de dienst ook geërft door die.
