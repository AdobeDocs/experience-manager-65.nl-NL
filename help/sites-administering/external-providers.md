---
title: Analyse met externe providers
seo-title: Analyse met externe providers
description: Meer informatie over Analytics met externe providers.
seo-description: Meer informatie over Analytics met externe providers.
uuid: 31a773ca-901e-45f2-be8f-951c26f9dbc5
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: bab465bc-1ff4-4f21-9885-e4a875c73a8d
docset: aem65
translation-type: tm+mt
source-git-commit: 90c99e527a40bb663d4f32d8746b46cf34a2319f
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# Analyse met externe providers {#analytics-with-external-providers}

Analyses kunnen u belangrijke en interessante informatie geven over het gebruik van uw website.

Verschillende configuraties buiten de box zijn beschikbaar voor integratie met de juiste service, bijvoorbeeld:

* [Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* [Adobe Target](/help/sites-administering/target.md)

U kunt uw eigen instantie van de **Algemene Fragmenten** van Analytics ook vormen om een nieuwe de dienstconfiguraties te bepalen.

De informatie wordt vervolgens verzameld door middel van kleine codefragmenten die aan de webpagina&#39;s worden toegevoegd. Bijvoorbeeld:

>[!CAUTION]
>
>Scripts mogen niet zijn opgenomen in `script` tags.

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
>De demosite Geometrixx-Buiten is zo geconfigureerd dat de kenmerken die worden opgegeven in de Pagina-eigenschappen worden toegevoegd aan de HTML-broncode (net boven de `</html>` eindtag) in het bijbehorende `js` script.
>
>Als uw eigen `/apps` niet van de standaardpaginacomponent ( `/libs/foundation/components/page`) erft moet u (of uw ontwikkelaars) ervoor zorgen dat de overeenkomstige `js` manuscripten inbegrepen zijn, bijvoorbeeld door of `cq/cloudserviceconfigs/components/servicescomponents`, of het gebruiken van een gelijkaardig mechanisme op te nemen.
>
>Zonder dit, zal geen van de diensten (Generic, Analytics, Target, etc.) werken.

## Een nieuwe service maken met een algemeen fragment {#creating-a-new-service-with-a-generic-snippet}

Voor de basisconfiguratie:

1. Open de **console van Hulpmiddelen** .
1. Vouw **Cloud Services Configurations** uit in het linkerdeelvenster.
1. Dubbelklik op **Generic Analytics Snippet** om de pagina te openen:

   ![](assets/analytics_genericoverview.png)

1. Klik op + om een nieuwe configuratie toe te voegen gebruikend de dialoog; minimaal een naam toewijzen, bijvoorbeeld google analytics:

   ![](assets/analytics_addconfig.png)

1. Klik op **Maken**, het dialoogvenster Fragment wordt direct geopend - plak het juiste JavaScript-fragment in het veld:

   ![](assets/analytics_snippet.png)

1. Klik op **OK** om op te slaan.

## Uw nieuwe service op pagina&#39;s gebruiken {#using-your-new-service-on-pages}

Nadat u de de dienstconfiguratie hebt gecreeerd moet u nu de vereiste pagina&#39;s vormen om het te gebruiken:

1. Navigeer naar de pagina.
1. Open de **Pagina-eigenschappen** vanuit sidekick en klik vervolgens op het tabblad **Cloud Services** .
1. Klik op Service **** toevoegen en selecteer de gewenste service. Bijvoorbeeld het **Generic Analytics-fragment**:

   ![](assets/analytics_selectservice.png)

1. Klik op **OK** om op te slaan.
1. U wordt teruggestuurd naar het tabblad **Cloud Services** . Het **Generic Analytics-fragment** wordt nu weergegeven met het bericht `Configuration reference missing`. Gebruik de drop-down lijst om uw specifiek de dienstgeval te selecteren; bijvoorbeeld google-analytics:

   ![](assets/analytics_selectspecificservice.png)

1. Klik op **OK** om op te slaan.

   Het fragment kan nu worden weergegeven als u de paginabron voor de pagina bekijkt.

   Nadat een geschikte periode is verstreken, kunt u de verzamelde statistieken bekijken.

   >[!NOTE]
   >
   >Als de configuratie aan een pagina in bijlage is die kindpagina&#39;s heeft, wordt de dienst ook geërft door die.
